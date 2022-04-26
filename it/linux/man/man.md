# man ZH

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