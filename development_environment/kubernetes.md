# Preparation for master & slave
## Update repository
```
$sudo apt update
```

## Turn off swap space
```
$sudo swapoff -a
```

// modify fstab
```
$sudo vi /etc/fstab
```
// add comment in front of the below line 
#/swapfile	none	swap	sw	0	0

## Update hostname, hosts and set static IP
// change host name to kmaster
```
$sudo vi /etc/hostname
```

// check ip address
```
$ifconfig
```
<networkId> ...

```
$sudo vi /etc/network/interfaces
```
// add the below after the last line, <networkId> can be obtained from 'ifconfig'
auto <networkId>
iface <networkId> inet static
address <your-ip>
// You have to use dhcp instead of static if you use DHCP
auto <networkId>
iface <networkId> inet dhcp

// modify hosts  
```
$sudo vi /etc/hosts
```
// add the below after the ip address line in both kmaster and knode
<ip-address>  kmaster
<ip_address>  knode
 
## Install OpenSSH server and Docker
```
$sudo apt install openssh-server
$sudo apt install -y docker.io
$sudo systemctl enable docker
$sudo start docker
$sudo usermod -aG docker <your-id>
```

## Install kubeadmin, kubelet, and kubectl
```
$sudo apt update
$sudo apt install -y apt-transport-https curl
$sudo su
$curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
$cat <<EOF >/etc/apt/sources.list.d/kubernetes.list
deb http://apt.kubernetes.io/ kubernetes-xenial main
EOF
$apt update
$apt install -y kubelet kubeadm kubectl
```

// update the kubernetes configuration
```
$vi /etc/systemd/system/kubelet.service.d/10-kubeadmin.conf
```
// add the below after environment 
Environment="cgroup-driver=systemd/cgroup-driver=cgroupfs"

```
$exit
```

# Master Installation

## Initiate Kubernetes cluster
// On Master
```
$sudo kubeadm init --pod-network-cidr=<> --apiserver-advertise-address=<ip-address-of-master>
```
// For starting a Calico CNI: 192.168.0.0/16 For starting a Flannel CNI: 10.244.0.0/16

// Keep the below that is the result of "kubeadmin init"
// This will be used for node's joining to a master
```
kubeadm join 192.168.1.48:6443 --token l3bmdu.y0i0yvnsbfx9ndx9 \
   --discovery-token-ca-cert-hash sha256:483764b6e9deadd519bff62e3f597925851f4656c39e16a4821768645f88351c
```

## Install the Pod networks

// To start using your cluster, you need to run the following as a regular user
```
$mkdir -p $HOME/.kube
$sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
$sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

// For creating a POD based on Calico
// https://docs.projectcalico.org/v3.7/getting-started/kubernetes/
```
$sudo kubectl apply -f https://docs.projectcalico.org/v3.7/manifests/calico.yaml
```

// verify PODs creation, select one of the belows 
```
$kubectl get pods -o wide --all-namespaces
$kubectl get pods --all-namespaces
```

## Setup the Kubernetes dashboard
// For creating the dashboard first - bring this up before starting Nodes
```
$kubectl create -f https://raw.githubusercontent.com/kubernetes/dashboard/v1.10.1/src/deploy/recommended/kubernetes-dashboard.yaml
```

// check the status of PODs
```
$kubectl get pods -o wide --all-namespaces
```
// To enable proxy and continue with new terminal window
```
$kubectl proxy
```

// To create a service account for your dashboard
```
$kubectl create serviceaccount dashboard -n default
```

// To add cluster binding rules for your roles on dashboard
```
$kubectl create clusterrolebinding dashboard-admin -n default --clusterrole=cluster-admin --serviceaccount=default:dashboard
```

// To get the secret key to be pasted to the dashboard token pwd.
// Copy the outcoming secret key
```
$kubectl get secret $(kubectl get serviceaccount dashboard -o jsonpath="{.secrets[0].name}") -o jsonpath="{.data.token}" | base64 --decode
```

// Kubernetes dashboard
http://localhost:8001
// Kubernetes login
http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/#!/login
// Token login
Paste the secret key

# Slave Installation

## Join the cluster
Join the cluster with the sentence you kept after run "kubeadm init"
```
$sudo kubeadm join <master-ip:port> --token <> --discovery-token-ca-cert-hash <hash>

