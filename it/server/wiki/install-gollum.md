# Install Gollum 
系统：Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-29-generic-pae i686)

1. 安装依赖包  
$ sudo apt-get update
$ sudo apt-get install git nano curl libicu-dev  

2. 为gollum创建一个用户  
$ sudo adduser --home /home/sunrise --shell /bin/bash  
$ sudo usermod -a -G sudo sunrise  

3. [安装ruby](/it/server/wiki/install-ruby-by-rvm)  
    3.1. 安装gollum  
        $ gem install -no-ri -no-rdoc gollum puma  
    3.2. 为gollum创建git仓库  
        $ git init gitrepo  
    3.3. 运行gollum  
        $ ~/.rvm/gems/ruby-2.4.6/gems/gollum-4.1.4/bin/gollum ~/workspaces/project/gollum/gitrepo/  
        "--live-preview" 选项能够让其一边修改一边预览

**源码安装**  
[参考gollum官方介绍](https://github.com/gollum/gollum)  
```
    $ git clone https://github.com/gollum/gollum
    $ cd gollum
    $ sudo bundle install (may not always be necessary).
    $ bundle exec bin/gollum
```

**以脚本的方式启动或关闭gollum程序**  
[参考gollum官方介绍](https://github.com/gollum/gollum/wiki/Gollum-as-a-service)  
1. Copy contrib/sysv-debian/init.d/gollum to /etc/init.d/ on your system.  
2. Adapt the GOLLUM_* variables to your needs: 
``` 
    GOLLUM_USER  设置成运行gollum的用户  
    GOLLUM_BASE  gollum运行依赖的git repos.  
    PID          用来lock的文件，可能是防止重复运行的。（注意运行用户对目录有写的权限）  
    LOG          保存运行gollum的日志 （注意运行用户对目录有写的权限）  
```
3. Make the script executable if it isn't already:  
    `chmod +x /etc/init.d/gollum`  
4. `/etc/init.d/gollum start` to start Gollum.
