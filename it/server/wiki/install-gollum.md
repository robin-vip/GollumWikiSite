系统：Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-29-generic-pae i686)

1. 安装依赖包  
$ sudo apt-get update
$ sudo apt-get install git nano curl libicu-dev  

2. 为gollum创建一个用户  
$ sudo adduser --home /home/sunrise --shell /bin/bash  
$ sudo usermod -a -G sudo sunrise  

3. [安装ruby](/it/server/install-ruby-by-rvm)  
    3.1. 安装gollum  
        $ gem install -no-ri -no-rdoc gollum puma  
    3.2. 为gollum创建git仓库  
        $ git init gitrepo  
    3.3. 运行gollum  
        $ ~/.rvm/gems/ruby-2.4.6/gems/gollum-4.1.4/bin/gollum ~/workspaces/project/gollum/gitrepo/  
        "--live-preview" 选项能够让其一边修改一边预览

