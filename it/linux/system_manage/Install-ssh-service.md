<h1>Install ssh service</h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)

1. 安装ssh server
```
# sudo apt-get install openssh-server
ssh 服务的配置文件是/etc/ssh/ssh_config，重启ssh服务的命令:
# sudo /etc/init.d/ssh restart
```

2. 安装ssh client (Ubuntu系统默认安装)
```
# sudo apt-get install openssh-client
```

3. ssh 登录
```
# ssh user_name@host_ip
```