<h1>Git mergetool</h1>

1. git配置
```
git config merge.tool vimdiff
git config merge.conflictstyle diff3
git config mergetool.prompt false
```

2. git mergetool 说明  
`LOCAL` -  文档来自当前分支；  
`BASE` - 两个分支的共同父节点；  
`REMOTE` - 要合并到你当前分支的外部分支上的文档；  
`MERGED` - 合并结果，将会保存到本地`repo`中;  
下面的命令从相应的文档获得相应的更改并将其放入到`MERGED`文档中
```
    :diffg RE              // get from REMOTE  
    :diffg BA              // get from BASE  
    :diffg LO              // get from LOCAL  
```