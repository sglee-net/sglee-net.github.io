You can meet the situation CentOS is stuck during boot after update packages.
The below is the process to fix it.

```
ctrl + alt + F2
log with shell prompt (ctrl+alt+F2) or ssh
$ sudo systemctl set-default multi-user.target
$ reboot
$ sudo yum -y update
$ sudo yum -y install kernel-devel epel-release
$ sudo yum -y install dkms gcc gcc-g++
$ reboot
$ sudo sh nvidia-driver-xx.run --no-opengl-files
$ sudo systemctl set-default graphical.target
$ reboot
```

