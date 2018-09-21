Client
```
$$$ ssh-keygen -t ecdsa -f ~/.ssh/id_ecdsa -b 521
$$$ ssh-copy-id -i ~/.ssh/id_ecdsa id@address
```

Sever
```
$ sudo vi sshd_config
  modify sshd_config
   - PubKeyAuthentification yes
   - PasswordAuthentification no
$ sudo systemctl restart sshd.service
```

Client
```
$ ssh -i ~/.ssh/id_ecdsa id@address
$ ssh id@address (server: PubKeyAuth yes)
```
