<h1>Git reset</h1>

**1. 指定文件替换暂存区的文件**
```
git reset [-q] [<commit>] [--] <paths>...
指定提交状态 (<commit>) 下的文件 (<paths>) 替换掉暂存区中的文件。
例如命令git reset HEAD <paths> 相当于取消之前执行的 git add <paths> 命令时改变的暂存区。
```
**2. 替换引用的指向，暂存区和工作区**
```
git reset --hard <commit> 
将引用指向指定的提交 (commit), 并将暂存区和工作区的内容变得和新引用指向的的目录树一致。
```
**3. 只更改引用的指向，不改变暂存区和工作区**
```
git reset --soft <commit>
```
**4. 更改引用的指向及重置暂存区，但不改变工作区**
```
git reset --mixed (可以不使用参数，默认为--mixed) <commit>
```