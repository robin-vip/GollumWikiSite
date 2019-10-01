<h1>Install Golang</h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)

1. 下载安装包
[go1.12.linux-386.tar.gz](https://dl.google.com/go/go1.12.linux-386.tar.gz) ([其它版本](https://golang.google.cn/dl/))

2. 安装  
$ tar -C /usr/local -xzf go1.12.linux-386.tar.gz

3. 配置
```
$ vi ~/.profile
```
将下面的内容添加到文件末尾
```
# set PATH so it includes user's go bin if it exists
if [ -d "/usr/local/go/bin" ] ; then
    PATH="/usr/local/go/bin:$PATH"
    export GOROOT=/usr/local/go
    export GOPATH=/usr/local/go/data/project
fi
```
让配置立即生效
```
$ source ~/.profile
```

参考  
* [Go 语言环境安装](https://www.runoob.com/go/go-environment.html)