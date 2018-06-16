#### Install Nvidia driver (Option for Nvidia graphic card)
1. go to nvidia site and download the driver (www.nvidia.com/object/unix.html)
   * Latest Long Lived Branch version
2. make the file executable
    ```
    $ cd ~/Downloads
    $ chmod +x NVIIDA-Linux-x86_64-3xx.run
    ```
3. change booting mode and reboot 
    ```
    $ sudo systemctl set-default multi-user.target
    ```
4. install driver with multi-user.target
    ```
    $ sudo ./NVIIDA-Linux-x86_64-3xx.run
    ```
5. you can see an error message, and Nvidia will create the modprobe to make blacklist of nouveau
    * select accept
6. disable nouveau
    ```
    $ sudo mv /boot/initramfs-$(uname -r).img /boot/initramfs-$(uname -r)-nvidia.img
    $ sudo dracut /boot/initramfs-$(uname -r).img $(uname -r)
    ```
7. reboot and install driver again

#### Update Repository
1. update yum 
    ```
    $ sudo yum -y update
    $ sudo yum -y install yum-utils
    ```
2. install epel repository
    ```
    $ sudo yum -y install epel-release
    ```
3. install ius repository
    ```
    $ sudo yum -y install https://centos7.iuscommunity.org/ius-release.rpm
    ```
4. update yum again
    ```
    $ sudo yum -y update
    ```
 *** important ***
 *** after update and upgrade, do step.0 process again

#### Install Cmake
1. goto https://cmake.org, and download the latest stable install file
2. tar -zxvf cmake-xxxversionxxx.tar.gz
3. cd cmake-xxxversionxxx
4. install
    ```
    $ ./bootstrap
    $ sudo make
    $ sudo make install
    ```

#### Install Java(openjdk), and modify environment 
1. search and install openjdk
    ```
    $ yum search openjdk
    $ sudo yum install java-1.8.0-openjdk
    $ sudo yum install java-1.8.0-openjdk-devel
    ```
2. add the below to .bash_profile
    ```
    $ JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk (or /etc/alternatives/java_sdk_1.8.0_openjdk)
    $ export JAVA_HOME
    ```

#### Install Maven
1. goto maven webpage(https://maven.apache.org), and download the binary install file
2. copy to /opt, and unzip the file
    ```
    $ sudo cp ~/Downloads/apache-maven-xxx.tar.gz /opt/
    $ cd opt
    $ sudo tar -zxvf apache-maven-xxx.tar.gz
    ```
3. make the link, and update environment
    ```
    $ sudo ln -s apache-maven-xxx maven
    $ vi ~/.bash_profile
    $ MAVEN_HOME=/opt/maven
    $ export PATH=$MAVEN_HOME/bin:$PATH
    ```

#### Install Ant
0. You can just install ant with apt on Ubuntu18.04
    ```
    $ sudo apt install ant
    ```
1. goto ant webpage(https://ant.apache.org), and download the binary install file
2. copy to /opt, and unzip the file
    ```
    $ sudo cp ~/Downloads/apache-ant-xxx.tar.gz /opt/
    $ cd opt
    $ sudo tar -zxvf apahce-ant-xxx.tar.gz
    ```
3. make the link, and update environment
    ```
    $ sudo ln -s apache-ant-xxx ant
    $ vi ~/.bash_profile
    $ ANT_HOME=/opt/ant
    $ export PATH=$ANT_HOME/bin:$PATH
    ```
    
#### Update Source
Centos: .bash_profile, Ubuntu: .profile
    ```
    $ source ~/.bash_profile
    ```

#### Install Environment(Python, other libraries) to install opencv
1. upgrade and update
    ```
    $ sudo yum update
    $ sudo yum upgrade
2. install python2xx and tools
    ```
    $ sudo yum install python-devel
    $ sudo yum install python-pip
    ```
3. install python36 and tools
CentOS7: python36u, Ubutu18.04: python3
    ```
    $ sudo yum -y install python36u
    $ sudo yum -y install python36u-devel
    $ sudo yum -y install python36u-pip
    ```
4. install python packages
    ```
    $ python --version (check the version of python2x)
    $ sudo pip install numpy (this is for version 2.7x)
    $ python3.6 --version (check the version of python3x)
    $ sudo pip3.6 install numpy (this is for version 3.6x)
    ```

#### Install OpenCV
1. install additional packages for opencv (CentOS, check the newest way)
    ```
    $ sudo yum install git pkgconfig (they maybe already installed)
    $ sudo yum install libpng-devel libjpeg-turbo-devel jasper-devel openexr-devel libtiff-devel libwebp-devel (to support various image format)
    $ sudo yum install libdc1394-devel libv4l-devel gstreamer-plugins-base-devel (for video format)
    $ sudo yum install tbb-devel eigen3-devel
    ```
    - just sudo apt install libopencv-dev on Ubuntu18.04
2. set virtual envirionment for opencv
3. install opencv

#### Install Boost and Thrift
1. install additional packages for thrift
    ```
    $ sudo yum install wget autoconf automake bison (maybe already installed)
    $ sudo yum install libevent-devel
    $ sudo yum install zlib-devel
    $ sudo yum install openssl-devel
    ```
2. go to the boost site (http://www.boost.org), and download the install file
3. unzip the downloaed file
    ```
    $ tar -zxvf boost_1_6xx.tar.gz
    ```
4. install boost
    ```
    $ cd boost_1_6xx
    $ sudo ./booststrap.sh
    $ sudo ./b2 install
    ```
5. install thrift
    ```
    $ git clone https://git-wip-us.apache.org/repos/asf/thrift.git
    $ cd thrift
    $ ./bootstrap.sh
    $ ./configure --with-lua=no
    $ make
    $ sudo make install
    ```
