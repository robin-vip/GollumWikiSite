<h1>git describe</h1>

<h2>一、 git describe 介绍</h2>
    git describe [--all][--tags][--contains][--abbrev=<n>][<commit-ish>…​]
    git describe [--all][--tags][--contains][--abbrev=<n>]--dirty[=<mark>]
    git describe <blob>

查找可以访问的提交的最新tag。 如果tag指向commit,则只显示tag。否则它的输出的名称为 "tag + 附加的提交数 + 最新的commit-ish"。

默认情况下（不带—all或—tags）`git describe` 仅显示带注释的tag。

<h2>二、  git describe 选项</h2>
* `<commit-ish>...`  
要描述的Commit-ish对象名称(也可以是分支名称)。如果省略，则默认为HEAD。

* `--all`  
不要只使用带注释的标签，而是使用refs/命名空间中的任何引用。此选项可以匹配任何已知分支，远程跟踪分支或轻量级标记。

* `--tags`  
不使用带注释的标签，而是使用refs/tags命名空间中的任何标签。此选项可以匹配轻量级（非注释）标记。

<h2>三、 利用git describe生成代码版本号</h2>
