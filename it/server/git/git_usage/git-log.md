<h1>Git log</h1>

1. **精简输出模式**
```
git log --pretty=oneline <file_name>
--pretty=oneline:  这个会输出完整的commit sha1值
--oneline:         这个只会输出commit sha1前几个字符(能够唯一标识的最短长度)
file_name:         查看指定文件的commit记录，如果没有指定文件名，会列出整个仓库的commit记录
```

2. **显示最近的几条日志**
```
可以使用参数-<n> (<n> 为数字), 显示最近的 <n> 条日志.
git log -3 --oneline
```

3. **显示每次提交的具体改动**
```
git log -p                 // 显示每次提交修改的详细内容
git log --stat             // 显示每次提交的变更概要
git log --name-only        // 显示每次修改的文件列表
git log --name-status      // 显示每次修改的文件列表和文件的修改状态（M:修改 A:新增文件 D:删除文件）
```

4. **显示某一个提交的变更**
```
git show [commit | tag] --stat   
可以显示提交或者tag的变更, 缺省是HEAD
--stat: 显示变更概要
```