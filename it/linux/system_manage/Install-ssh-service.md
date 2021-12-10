<h1>Install ssh service</h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)

##  安装  
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

##  FAQ
1. SecureCRT 6.5.0 连接 ubuntu 20.04 LTS时失败，具体错误信息如下：
```
Key exchange failed. 
No compatible key exchange method. The server supports these methods: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256


Press Ctrl+c to cancel or Enter to reconnect immediately.
```
解决方法是让ubuntu支持旧的密钥交换方式
```
sudo vim /etc/ssh/sshd_config
添加一下一行文本:
KexAlgorithms curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha1,diffie-hellman-group-exchange-sha1,diffie-hellman-group1-sha1
重启ssh server
sudo service ssh restart
```
