<h1>Git tag</h1>

<h2>tag 介绍</h2>
tag是git版本库的一个标记，指向某个git commit。  

通常用于发布版本的管理，一个版本发布之后，我们可以为git打上 v.1.0.1 v.1.0.2 ...这样的tag。  

tag类似与branch, 但不同的是，tag被创建后不会再有commit提交。 branch对应一系列commit，是很多点连成的一根线，有一个HEAD 指针，是可以依靠 HEAD 指针移动的。

<h2>tag 用法</h2>
1. **创建tag**  
git tag有两种：一种是轻量级的，另一种是带注释的。  
* **创建轻量级tag**
```
git tag <tagname>  // tagnanme通常版本号：v1.x.x  

这个是轻量级tag，没有注释，仅仅指向当前branch HEAD指向的commit.
```
* **创建带注释tag**
```
git tag -a v1.4

执行这条命令后，会打开默认配置的文本编辑器，可以输入其它备注信息，例如，email, 时间等。也可以用下面的命令：

git tag -a v1.4 "my version v1.4"

类似于git commit 和 git commit -m
```
* **指定tag的为任意commit SHA hash**
```
git tag -a v1.2 15027957951b64cf874c3557a0f3547bd83b3f13
```
* **修改tag指向的commit**
```
git tag -a -f v1.4 15027957951b64cf874c3557a0f3547bd83b3f13
tag v1.4 已经存在，-f 选项可以强制指定其它的commit.
```

2. **推送tag**
* **push 指定的tag**
```
git push origin <tagname>
```
* **push 所有tags**
```
git push origin --tags
```

3. **查看tag**
* **查看指定的tag**
```
git show <tagname>
```
* **列出所有本地的tags**
```
git tag 或 git tag -l
```
* **列出所有远程的tags**
```
git ls-remote --tags origin
```

4. **删除tag**
* **删除本地tag**
```
git tag -d <tagname>
```
* **删除远程tag**
```
git tag -d v1.4
git push origin :refs/tags/v1.4
先删除本地，再删除远程的
```

5. **checkout tag**
```
git checkout -b <new-branch-name> <tagname>
这条命令会在新的分支上checkout tag, 如果不指定分支名也是可以的，只是会处于 detached HEAD状态。
```

<h2>扩展： </h2> 
* git tag 配合 git describe 可以生成仓库代码的版本号