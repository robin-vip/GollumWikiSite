<h1>Git usage</h1>

1. 删除文件
```
a. 只删除暂存区文件
git rm --cached <file>
```

2. git log
```
a. 精简输出模式
git log --pretty=oneline

```

3. git checkout
```
a. 用暂存区全部的文件替换工作区的文件
git checkout .

b. 用暂存区指定的文件替换工作区的文件
git checkout -- <file>

c. 用HEAD指向分支版本库全部的文件替换工作区的文件
git checkout HEAD .

d. 用HEAD指向分支版本库指定文件替换工作区的文件
git checkout HEAD <file>
```

4. git diff
```
a. 工作区与暂存区比较  git diff

b. 暂存区与HEAD比较  git diff --cached

c. 工作区与HEAD比较  git diff HEAD
```




