https://docs.docker.com/install/linux/linux-postinstall//#configure-docker-to-start-on-boot

# Register Service

## Make Service
Docker service is already made.
```
  $ vi /etc/systemd/system/<myservice>.service
```
```
  [Unit]
  Description=Docker Service
  Requires=docker.service
  After=docker.service

  [Service]
  Type=always
  ExecStart=/opt/service/service.sh

  [Install]
  WantedBy=default.target
```

## Enable Service
```
  $ sudo systemctl enable docker
```

## Start Service
```
  $ sudo systemctl start docker
```

# Run Container on Boot
## Modify Service File
```
  ExecStart=/usr/bin/docker start docker_container_name
  ExecStop=/usr/bin/docker stop docker_container_name
```
