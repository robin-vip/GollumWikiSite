系统：Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-29-generic-pae i686)

rvm 安装主要参考这两个链接：  
[Installing RVM](http://www.rvm.io/rvm/install)  
[Install rvm on ubuntu](https://github.com/rvm/ubuntu_rvm)

1. 安装RVM(参照第二个链接)  
    1.1. 安装 software-properties-common  
    $ sudo apt-get install software-properties-common  
    1.2. 添加PPA安装RVM  
    $ sudo apt-add-repository -y ppa:rael-gc/rvm  
    $ sudo apt-get update  
    $ sudo apt-get install rvm

2. 安装ruby  
    2.1. 安装RVM依赖  
        $ rvm requirements  
    2.2. 列出可用的ruby版本  
        $ rvm list known  
    2.3. 安装ruby-2.4.6  
        $ rvm install 2.4.6  
    2.4. 设置ruby默认使用的版本  
        $ rvm use 2.4.6 --default  
    2.5. 安装rails  
        $ gem install rails
