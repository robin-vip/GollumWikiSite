<h1>Git init</h1>

<h3>cmd: git init [--bare]</h3>
```
初始化创建一个空仓库， --bare 初始化一个裸git仓库。
```

<h3>git init 与git init --bare区别</h3>
```
git init 初始化的仓库，目录下只有一个 .git 隐藏文件夹，里面包含各种信息，而 git init --bare 
表示创建一个裸库，主要应用场景是作为公共仓库。

裸库的目录下没有隐藏 .git 目录，全都是显示的，没有 .git 这个目录，进入文件直接是文件内容，一般
来讲，作为远端备份或公共版本库时，应该使用 git init --bare。

git init –bare 方法创建一个所谓的裸仓库，之所以叫裸仓库是因为这个仓库只保存 git 历史提交的版本
信息，而不允许用户在上面进行各种 git 操作，如果你硬要操作的话，只会得到下面的错误
（”This operation must be run in a work tree”）。
```