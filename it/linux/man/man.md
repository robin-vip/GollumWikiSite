# man 手册

## 安装C语言库函数基本的帮助文档
```
sudo apt-get install manpages
sudo apt-get install manpages-de
sudo apt-get install manpages-de-dev
sudo apt-get install manpages-dev
```

## 安装POSIX函数帮助文档
```
sudo apt-get install manpages-posix
sudo apt-get install manpages-posix-dev
```

## 安装内核函数手册
```
sudo apt-get install linux-doc
```

## 安装man中文手册
1. 安装中文man手册
```
sudo apt-get install manpages-zh
```

2. 编辑~/.bashrc, 添加下面的命令
```
alias cman='man -M /usr/share/man/zh_CN'
```
* 和系统原来的man区分开，用alias给中文man的命令设置一个别名
* 使用“dpkg -L manpages-zh | less” 命令查看中文man手册安装路径

## 使用man手册
|section|description|  
|----|----|  
|1. Standard commands|Executable programs or shell commands|
|2. System calls|System calls (functions provided by the kernel)|

1. 系统函数
```
man 2 open
```

2. 标准库
```
man 3 perror
```
