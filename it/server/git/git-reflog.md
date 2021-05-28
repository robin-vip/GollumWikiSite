<h1>Git reflog</h1>


1. 可以查看所有分支的所有操作记录 （包括已经被删除的commit记录和reset的操作）

2. Git 通过.git/logs目录下日志文件记录了HEAD, 分支的变更。默认非裸版本库（带有工作区）都提供HEAD, 分支日志功能，这是因为带有
工作区的版本库都有如下设置：  
```
$ git config core.logallrefupdates
true
```
master分支对应文件.git/logs/refs/heads/master, 其它分支也是类似的.

3. 显示指定分支的操作记录
```
$ git reflog show master | head -5
afe4749 master@{0}: pull origin: Fast-forward
226ba04 master@{1}: pull: Fast-forward
53e0c80 master@{2}: pull: Fast-forward
4d380da master@{3}: pull: Fast-forward
6f19a7a master@{4}: pull: Fast-forward
```
git reflog 后面不接show branch会打印 HEAD的变更记录
