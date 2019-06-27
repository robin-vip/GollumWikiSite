<h1>Install mm WiKi</h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)

1. [安装mysql](/it/mysql/Install-Mysql).  
2. 下载mm_wiki安装包  
```
# https://github.com/phachon/mm-wiki/releases   （mm-wiki-linux-386.tar.gz）  
$ cd install
# 执行安装程序，默认端口为 8090，指定其他端口加参数 --port=8087
$ ./install
# 浏览器访问 http://ip:8090 进入安装界面，完成安装配置
# Ctrl + C 停止 install 程序, 启动 MM-Wiki 系统
$ cd ..
$ ./mm-wiki --conf conf/mm-wiki.conf
# 浏览器访问你监听的 ip 和端口
# 开始 MM-Wiki 的使用之旅吧！
```

[mm wiki 入口](http://192.168.2.135:8080/)
