# Setting for SSH server and client

## Server
```
$sudo apt update
$sudo apt install openssh-server
```

## Client
```
$ssh-keygen -t ecdsa -f ~/.ssh/id_ecdsa -b 521
$ssh-copy-id -i ~/.ssh/id_ecdsa id@address
```

## Sever
modify sshd_config
```
PubKeyAuthentification yes
PasswordAuthentification no
```
```
$sudo systemctl restart sshd.service
```

## Client
```
$ssh -i ~/.ssh/id_ecdsa id@address
$ssh id@address (server: PubKeyAuth yes)
```
