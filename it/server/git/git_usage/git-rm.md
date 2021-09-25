<h1>Git rm</h1>

1. **git rm**
    * 将文件从暂存区和工作区中删除
```
git rm <file>
```
如果删除之前修改过并且已经放到暂存区域的话，则必须要用强制删除选项`-f`  
```
git rm -f <file>
```

    * 只删除暂存区文件
```
git rm --cached <file>
```

    * `-r`选项可以递归删除
```
git rm -r <--cached> <directory>
```

2. **git clean 用于删除没有track过的文件**
    * 查看哪些文件和目录会被删除
```
git clean -nd

参数说明：
n: 显示将要被删除的文件
d: 除了文件外，还删除目录 （如果未跟踪的目录被其它repository管理，这需要加两次 '-f' 选项才能删除）
```
    * 强制删除多余的目录和文件
```
git clean -fd

参数说明：
f: 强制运行
```