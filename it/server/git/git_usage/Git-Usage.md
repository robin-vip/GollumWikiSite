<h1>Git usage</h1>

<h2>Git command</h2>
1. [git init](/it/server/git/git_usage/git-init)

1. [git rm](/it/server/git/git_usage/git-rm)

2. [git log](/it/server/git/git_usage/git-log)

3. [git reflog](/it/server/git/git_usage/git-reflog)

4. [git add](/it/server/git/git_usage/git-add)

5. [git checkout](/it/server/git/git_usage/git-checkout)

6. [git reset](/it/server/git/git_usage/git-reset)

7. [git cherry-pick](/it/server/git/git_usage/git-cherry-pick) 

8. [git clean](/it/server/git/git_usage/git-clean)

9. [git diff](/it/server/git/git_usage/git-diff)

10. [git stash](/it/server/git/git_usage/git-stash)

11. [git archive](/it/server/git/git_usage/git-archive)

12. [git rebase](/it/server/git/git_usage/git-rebase)

13. [git tag](/it/server/git/git_usage/git-tag)

<h2>Git settings</h2>
* git config 简介
```
git config的配置级别有三类：
1. 系统级别 system (优先级最低)   配置文件路径：/etc/gitconfig
2. 用户级别 global （优先级稍高） 配置文件路径：~/.gitconfig （用户Home目录下）
3. 仓库级别 local  (优先级最高)   配置文件路径：.git/config  (仓库目录下)
```

* 显示当前git config信息
```
git config --system -l               显示系统设置
git config --global -l               显示全局设置
git config --local  -l               显示当前目录仓库设置
```

* git config -e 直接编辑配置文件
```
git config --system -e               编辑系统级别配置文件
git config --global -e               编辑用户级别配置文件
git config --local -e                编辑仓库级别配置文件
```

* 增加配置项
```
git config [--local|--global|--system] --add section.key value
Notes: 
    1. 默认是添加在local配置中;
    2. add后面的section,key,value一项都不能少，否则添加失败;
```

* 获取配置项
```
git config [--local|--global|--system] --get section.key
```

* 删除配置项
```
git config [--local|--global|--system] --unset section.key
```

* 设置用户信息(用户名和邮箱)
```
git config --global user.name "Robin"
git config --global user.email Robin@qq.com

对特定的库做单独的设置(当前目录所在的仓库)
git config user.name "sunrise"
git config user.email sunrise@qq.com
```

* 设置编辑器
```
git config --global core.editor vim        设置git编辑器为vim
```

* 设置注释字符  
  在一些工单系统中，一般工单是以"#issue_id"的格式。 git commit命令
  在备注提交comment时，一般都需要标明工单。但一般的编辑器是把'#'当
  作注释符号的。为了不引起冲突，可以用下面的命令，将注释符号改成别
  的字符。
```
git config --global core.commentChar ";"    将注释符号设置成';'字符
```

* 格式化与多余空白字符  
  `core.autocrlf`  
  多人协作时，因为编辑器不同或者系统不同可能会遇到LF, CRLF问题。
  Git可以在提交时自动地把回车换行转换成换行，而在检出代码时会把
  换行转换成回车和换行。 
  这种情况下，可以设置`core.autocrlf`来打开此项功能。
```
git config --global core.autocrlf true     提交时自动地把回车换行转换成换行,检出代码时会把换行转换成回车和换行
git config --global core.autocrlf input    在提交时把回车和换行转换成换行，检出时不转换
```

  `core.whitespace`  
  Git 预先设置了一些选项来探测和修正多余空白字符问题。它提供了六种
  处理多余空白字符的主要选项—— 其中三个默认开启，另外三个默认关闭。
  默认被打开的三个选项是：
```
blank-at-eol        查找行尾的空格
blank-at-eof        盯住文件底部的空行
space-before-tab    警惕行头 tab 前面的空格
```
  默认被关闭的三个选项是:
```
indent-with-non-tab    揪出以空格而非 tab 开头的行（你可以用 tabwidth 选项控制它）
tab-in-indent          监视在行头表示缩进的 tab
cr-at-eol              告诉 Git 忽略行尾的回车
```
  通过设置 core.whitespace，你可以让 Git 按照你的意图来打开或关闭以
  逗号分割的选项。 要想关闭某个选项，你可以在输入设置选项时不指定它
  或在它前面加个 -。 例如，如果你想要打开除`space-before-tab` 之外
  的所有选项，那么可以这样 （ trailing-space 涵盖了 blank-at-eol 
  和 blank-at-eof ）：
```
$ git config --global core.whitespace \
    trailing-space,-space-before-tab,indent-with-non-tab,tab-in-indent,cr-at-eol
```
你也可以只指定自定义的部分：
```
$ git config --global core.whitespace \
    -space-before-tab,indent-with-non-tab,tab-in-indent,cr-at-eol
```
  当你运行 git diff 命令并尝试给输出着色时，Git 将探测到这些问题，
  因此你在提交前就能修复它们。




  


