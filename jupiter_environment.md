# How to use Jupiter

## 1. Install Python3
```
$sudo apt install python3
```

## 2. Install Jupiter
```
$sudo apt install Jupiter
$jupiter notebook
```

## 3. Run Jupiter as a service
### make a service file
```
$cd /etc/systemd/system
$vi jupyter.service
```
jupyter.service
```
[Unit]
Description=jupyter notebook

[Service]
User = user
Group = user
WorkingDirectory=/home/user/workspace_jupyter

ExecStart=/bin/bash -c "/opt/jupyter/jupyter.sh --config=/opt/jupyter/jupyter_notebook_config.py"

TimeoutStopSec = 10
Restart=on-failure
RestartSec=5

[Install]
WantedBy=multi-user.target
```
make a shell scipt and give write permission
```
$sudo mkdir /opt/jupyter
$vi /opt/jupyter/jupyter.sh
$sudo chmod 755 jupyter.sh
```
  jupyter.sh
  ```
  #!bin/bash
  jupyter notebook --config /opt/jupyter/jupyter_notebook_config.py
  ```

make a config file and copy it to the installation folder
```
$cd ~/
$jupyter notebool --generate-config
$sudo cp ./jupyter_notebook_config.py /opt/jupyter
```
