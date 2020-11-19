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

4. git reset
    + 指定文件替换暂存区的文件
```
git reset [-q] [<commit>] [--] <paths>...
指定提交状态 (<commit>) 下的文件 (<paths>) 替换掉暂存区中的文件。
例如命令git reset HEAD <paths> 相当于取消之前执行的 git add <paths> 命令时改变的暂存区。
```
    + 替换引用的指向，暂存区和工作区
```
git reset --hard <commit> 
将引用指向指定的提交 (commit), 并将暂存区和工作区的内容变得和新引用指向的的目录树一致。
```
    + 只更改引用的指向，不改变暂存区和工作区
```
git reset --soft <commit>
```
    + 更改引用的指向及重置暂存区，但不改变工作区
```
git reset --mixed (可以不使用参数，默认为--mixed) <commit>
```

5. git clean
    * 查看哪些文件和目录会被删除
```
git clean -nd
```
    * 强制删除多余的目录和文件
```
git clean -fd
```

6. git diff
```
a. 工作区与暂存区比较  git diff

b. 暂存区与HEAD比较  git diff --cached

c. 工作区与HEAD比较  git diff HEAD
```

7. git stash
```
git stash save "save message"    保存当前的工作状态，并添加备注

git stash list                   查看有哪些stash

git stash show                   显示做了哪些改动，默认show第一个存储,如果要显示其他存贮，后面加stash@{$num}，比如第二个 git stash show stash@{1}

git stash apply                  应用某个存储,但不会把存储从存储列表中删除，默认使用第一个存储,即stash@{0}，如果要使用其他个，git stash apply stash@{$num} ， 比如第二个：git stash apply stash@{1} 

git stash pop                    命令恢复之前缓存的工作目录，将缓存堆栈中的对应stash删除，并将对应修改应用到当前的工作目录下,默认为第一个stash,即stash@{0}，如果要应用并删除其他stash，命令：git stash pop stash@{$num} ，比如应用并删除第二个：git stash pop stash@{1}

git stash drop stash@{$num}      丢弃stash@{$num}存储，从列表中删除这个存储

git stash clear                  删除所有缓存的stash
```

8. git archive
```
一般的压缩工具（tar，7zip， Winzip， rar等）在工作区归档时可能会将版本库（.git目录）包含其中，甚至将工作区的忽略文件，
临时文件也包含其中。git archive 可以避免这种情况。
```
    * git archive 支持的归档文件格式
```
$ git archive -l
tar
tgz
tar.gz
zip
```
    * 归档分支或commit
```
git archive --format tar.gz --output "output.tar.gz" master
master: 将master分支归档， 可以是commit id, 或者HEAD.
--format: 指定归档文件格式，如不指明此项，则根据--output中的文件名推断文件格式.
```
    * 归档指定文件,目录
```
git archive -o output.tar.gz HEAD myfile mydir1 mydir2
```
    * 基于tag归档
```
git archive --format=tar --prefix=1.0/ v1.0 | gzip > output-1.0.tar.gz
基于tag v1.0 建立归档，并且归档中的文档添加目录前缀 1.0
```





