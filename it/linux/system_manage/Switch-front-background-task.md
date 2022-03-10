# Switch front background task

## 切换到后台
* 在 linux 终端运行命令的时候，在命令末尾加上 & 符号，就可以让程序在后台运行
```
hw_testkit_app &
```

* Ctrl+z 将前台运行的程序暂停，然后用 bg %[number] 切换到后台运行

## 切换到前台
* job -l 查看正在运行的程序(获取number)，然后用 fg %[number] 切换到前台运行

## 相关命令说明
1. &  
加在一个命令的最后，可以把这个命令放到后台执行

2. ctrl + z 
将一个正在前台运行的程序切换到后台，并且处于暂停状态 (可以用bg %[number] 切换到后台运行)

3. fg
将后台的程序切换到前台运行。如果后台有多个程序，可以用fg %[number] (是程序编号，不是进程号)切换前台

4. bg
将后台暂停的程序，切换到后台运行。如果后台有多个程序，可以用bg %[number] 

5. kill
* 通过jobs命令查看job号（假设为num），然后执行kill %num
* 通过ps命令查看job的进程号（PID，假设为pid），然后执行kill pid

6. nohup
如果让程序始终在后台执行，即使关闭当前的终端也执行（之前的&做不到），这时候需要nohup。
该命令可以在你退出帐户/关闭终端之后继续运行相应的进程。
关闭终端后，在另一个终端jobs已经无法看到后台跑得程序了，此时利用ps（进程查看命令）