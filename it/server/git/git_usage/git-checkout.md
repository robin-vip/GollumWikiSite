<h1>Git checkout</h1>

1. 切换分支
```
git checkout [<branch>]
```

2. 创建分支
```
git checkout -b <branch>
git checkout -B <branch>        // 强制创建分支，不管是否已经同名分支
```

3. 用暂存区全部的文件替换工作区的文件
```
git checkout .
```

4. 用暂存区指定的文件替换工作区的文件
```
git checkout -- <file>
```

5. 用HEAD指向分支版本库全部的文件替换工作区的文件
```
git checkout HEAD .
```

6. 用HEAD指向分支版本库指定文件替换工作区的文件
```
git checkout HEAD <file>
```

7. 基于当前所在分支新建一个没有commit记录的分支
```
git checkout --orphan <branch>
```
