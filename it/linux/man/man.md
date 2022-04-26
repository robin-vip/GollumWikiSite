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
|1. Standard commands|Executable programs or shell commands 可执行程序或shell命令|
|2. System calls|System calls (functions provided by the kernel) 系统调用（由内核提供的函数）|  
|3. Library calls|Library calls (functions within program libraries) 库调用 （标准库或第三方库提供的函数）|  
|4. Special devices|Special files (usually found in /dev) 特殊文件（如对文件/dev/random的描述 ）|  
|5. File formats|File formats and conventions eg /etc/passwd 描述了文件的格式，各个字段的含义和取值约束等|  
|6. Games and toys|Games 游戏|  
|7. Miscellaneous|Miscellaneous (including macro packages and conventions), e.g. man(7), groff(7) 杂项（不便具体分类的说明都暂且都放这节）|  
|8. Administrative Commands|System administration commands (usually only for root) 系统管理员命令（通常仅适用于root用户）|  
|9. Kernel routines [Non standard]|Kernel routines [Non standard] 内核例程（非标准）|  

1. 系统函数
```
man 2 open
```

2. 标准库
```
man 3 perror
```
