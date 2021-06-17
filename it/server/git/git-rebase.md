<h1>Git rebase</h1>

* 修改之前的某个提交
```
a. git stash save "stash_message"   //将工作去修改加入stash
b. git rebase -i commit_hash        // commit_hash是需要修改的commit的前一个commit
这个命令执行完之后会有提示需要修改哪些commits, 以及应该怎么修改；修改之后保存退出。
c. git stash apply stash@{idx}      // 将stash中的修改返回到工作区
d. git add filename                 // 添加修改的文件到暂存区
e. git commit --amend               // 如果需要修改commit message的话用git commit -m "commit_message"命令
f. git rebase --continue            // 接着处理其它需要修改的commit，完成后会有类似下面的提示
"Successfully rebased and updated refs/heads/development."
``` 