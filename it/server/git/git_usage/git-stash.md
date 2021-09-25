<h1>Git stash</h1>

```
git stash save "save message"    保存当前的工作状态，并添加备注 (可能会慢慢被 git stash push替代)

git stash list                   查看有哪些stash

git stash show                   显示做了哪些改动，默认show第一个存储,如果要显示其他存贮，后面加stash@{$num}，比如第二个 git stash show stash@{1}

git stash apply                  应用某个存储,但不会把存储从存储列表中删除，默认使用第一个存储,即stash@{0}，如果要使用其他个，git stash apply stash@{$num} ， 比如第二个：git stash apply stash@{1} 

git stash pop                    命令恢复之前缓存的工作目录，将缓存堆栈中的对应stash删除，并将对应修改应用到当前的工作目录下,默认为第一个stash,即stash@{0}，如果要应用并删除其他stash，命令：git stash pop stash@{$num} ，比如应用并删除第二个：git stash pop stash@{1}

git stash drop stash@{$num}      丢弃stash@{$num}存储，从列表中删除这个存储

git stash clear                  删除所有缓存的stash
```