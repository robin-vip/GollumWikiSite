<h1>Git usage</h1>

1. 删除文件
```
a. 只删除暂存区文件
git rm --cached <file>
```

2. git log
    * 精简输出模式
```
git log --pretty=oneline
--pretty=oneline:  这个会输出完整的commit sha1值
--oneline:         这个只会输出commit sha1前几个字符(能够唯一标识的最短长度)
```
    * 显示最近的几条日志
```
可以使用参数-<n> (<n> 为数字), 显示最近的 <n> 条日志.
git log -3 --oneline
```
    * 显示每次提交的具体改动
```
git log -p                 // 显示每次提交修改的详细内容
git log --stat             // 显示每次提交的变更概要
```
    * 显示某一个提交的变更
```
git show [commit | tag] --stat   
可以显示提交或者tag的变更, 缺省是HEAD
--stat: 显示变更概要
```

2. git reflog
```
Git 通过.git/logs目录下日志文件记录了HEAD, 分支的变更。默认非裸版本库（带有工作区）都提供HEAD, 分支日志功能，这是因为带有
工作区的版本库都有如下设置：
$ git config core.logallrefupdates
true
master分支对应文件.git/logs/refs/heads/master, 其它分支也是类似的.

$ git reflog show master | head -5
afe4749 master@{0}: pull origin: Fast-forward
226ba04 master@{1}: pull: Fast-forward
53e0c80 master@{2}: pull: Fast-forward
4d380da master@{3}: pull: Fast-forward
6f19a7a master@{4}: pull: Fast-forward

git reflog 后面不接show branch会打印 HEAD的变更记录
```

3. git add
* git add -i  交互式暂存  
当在修改了大量文件后，希望这些改动能拆分为若干提交而不是混杂在一起成为一个提交时，这几个工具会非常有用。 通过这种方式，可以确保提交是逻辑上独立的变更集，同时也会使其他开发者在与你工作时很容易地审核。 如果运行 git add 时使用 -i 或者 --interactive 选项，Git 将会进入一个交互式终端模式，显示类似下面的东西：
```
$ git add -i
           staged     unstaged path
  1:    unchanged        +0/-1 TODO
  2:    unchanged        +1/-1 index.html
  3:    unchanged        +5/-1 lib/simplegit.rb

*** Commands ***
  1: [s]tatus     2: [u]pdate      3: [r]evert     4: [a]dd untracked
  5: [p]atch      6: [d]iff        7: [q]uit       8: [h]elp
What now>
```
可以看到这个命令以和平时非常不同的视图显示了暂存区——基本上与 git status 是相同的信息，但是更简明扼要一些。 它将暂存的修改列在左侧，未暂存的修改列在右侧。  
在这块区域后是“Commands”命令区域。 在这里你可以做一些工作，包括暂存文件、取消暂存文件、暂存文件的一部分、添加未被追踪的文件、显示暂存内容的区别。  
**暂存与取消暂存文件**  
如果在 What now> 提示符后键入 u 或 2（更新），它会问你想要暂存哪个文件：
```
What now> u
           staged     unstaged path
  1:    unchanged        +0/-1 TODO
  2:    unchanged        +1/-1 index.html
  3:    unchanged        +5/-1 lib/simplegit.rb
Update>>
```
要暂存 TODO 和 index.html 文件，可以输入数字：
```
Update>> 1,2
           staged     unstaged path
* 1:    unchanged        +0/-1 TODO
* 2:    unchanged        +1/-1 index.html
  3:    unchanged        +5/-1 lib/simplegit.rb
Update>>
```
每个文件前面的 * 意味着选中的文件将会被暂存。 如果在 Update>> 提示符后不输入任何东西并直接按回车，Git 将会暂存之前选择的文件：
```
Update>>
updated 2 paths

*** Commands ***
  1: [s]tatus     2: [u]pdate      3: [r]evert     4: [a]dd untracked
  5: [p]atch      6: [d]iff        7: [q]uit       8: [h]elp
What now> s
           staged     unstaged path
  1:        +0/-1      nothing TODO
  2:        +1/-1      nothing index.html
  3:    unchanged        +5/-1 lib/simplegit.rb
```
现在可以看到 TODO 与 index.html 文件已经被暂存而 simplegit.rb 文件还未被暂存。 如果这时想要取消暂存 TODO 文件，使用 r 或 3（撤消）选项：
```
*** Commands ***
  1: [s]tatus     2: [u]pdate      3: [r]evert     4: [a]dd untracked
  5: [p]atch      6: [d]iff        7: [q]uit       8: [h]elp
What now> r
           staged     unstaged path
  1:        +0/-1      nothing TODO
  2:        +1/-1      nothing index.html
  3:    unchanged        +5/-1 lib/simplegit.rb
Revert>> 1
           staged     unstaged path
* 1:        +0/-1      nothing TODO
  2:        +1/-1      nothing index.html
  3:    unchanged        +5/-1 lib/simplegit.rb
Revert>> [enter]
reverted one path
```
再次查看 Git 状态，可以看到已经取消暂存 TODO 文件：
```
*** Commands ***
  1: [s]tatus     2: [u]pdate      3: [r]evert     4: [a]dd untracked
  5: [p]atch      6: [d]iff        7: [q]uit       8: [h]elp
What now> s
           staged     unstaged path
  1:    unchanged        +0/-1 TODO
  2:        +1/-1      nothing index.html
  3:    unchanged        +5/-1 lib/simplegit.rb
```
如果想要查看已暂存内容的区别，可以使用 d 或 6（区别）命令。 它会显示暂存文件的一个列表，可以从中选择想要查看的暂存区别。 这跟你在命令行指定 git diff --cached 非常相似：
```
*** Commands ***
  1: [s]tatus     2: [u]pdate      3: [r]evert     4: [a]dd untracked
  5: [p]atch      6: [d]iff        7: [q]uit       8: [h]elp
What now> d
           staged     unstaged path
  1:        +1/-1      nothing index.html
Review diff>> 1
diff --git a/index.html b/index.html
index 4d07108..4335f49 100644
--- a/index.html
+++ b/index.html
@@ -16,7 +16,7 @@ Date Finder

 <p id="out">...</p>

-<div id="footer">contact : support@github.com</div>
+<div id="footer">contact : email.support@github.com</div>

 <script type="text/javascript">
```
通过这些基本命令，可以使用交互式添加模式来轻松地处理暂存区。  
**暂存补丁**  
Git 也可以暂存文件的特定部分。 例如，如果在 simplegit.rb 文件中做了两处修改，但只想要暂存其中的一个而不是另一个，Git 会帮你轻松地完成。 在和上一节一样的交互式提示符中，输入 p 或 5（补丁）。 Git 会询问你想要部分暂存哪些文件；然后，对已选择文件的每一个部分，它都会一个个地显示文件区别并询问你是否想要暂存它们：
```
diff --git a/lib/simplegit.rb b/lib/simplegit.rb
index dd5ecc4..57399e0 100644
--- a/lib/simplegit.rb
+++ b/lib/simplegit.rb
@@ -22,7 +22,7 @@ class SimpleGit
   end

   def log(treeish = 'master')
-    command("git log -n 25 #{treeish}")
+    command("git log -n 30 #{treeish}")
   end

   def blame(path)
Stage this hunk [y,n,a,d,/,j,J,g,e,?]?
```
这时有很多选项。 输入 ? 显示所有可以使用的命令列表：
```
Stage this hunk [y,n,a,d,/,j,J,g,e,?]? ?
y - stage this hunk                                                       暂存此区块   
n - do not stage this hunk                                                不暂存此区块
q - quit; do not stage this hunk or any of the remaining ones             退出；不暂存包括此块在内的剩余的区块
a - stage this and all the remaining hunks in the file                    暂存此块与此文件后面所有的区块
d - do not stage this hunk nor any of the remaining hunks in the file     不暂存此块与此文件后面所有的 区块
g - select a hunk to go to                                                选择并跳转至一个区块
/ - search for a hunk matching the given regex                            搜索与给定正则表达示匹配的区块
j - leave this hunk undecided, see next undecided hunk                    暂不决定，转至下一个未决定的区块
J - leave this hunk undecided, see next hunk                              暂不决定，转至一个区块
k - leave this hunk undecided, see previous undecided hunk                暂不决定，转至上一个未决定的区块
K - leave this hunk undecided, see previous hunk                          暂不决定，转至上一个区块
s - split the current hunk into smaller hunks                             将当前的区块分割成多个较小的区块
e - manually edit the current hunk                                        手动编辑当前的区块
? - print help                                                            输出帮助
```
通常情况下可以输入 y 或 n 来选择是否要暂存每一个区块， 当然，暂存特定文件中的所有部分或为之后的选择跳过一个区块也是非常有用的。 如果你只暂存文件的一部分，状态输出可能会像下面这样：
```
What now> 1
           staged     unstaged path
  1:    unchanged        +0/-1 TODO
  2:        +1/-1      nothing index.html
  3:        +1/-1        +4/-0 lib/simplegit.rb
```
simplegit.rb 文件的状态很有趣。 它显示出若干行被暂存与若干行未被暂存。 已经部分地暂存了这个文件。 在这时，可以退出交互式添加脚本并且运行 git commit 来提交部分暂存的文件。  
也可以不必在交互式添加模式中做部分文件暂存——可以在命令行中使用 git add -p 或 git add --patch 来启动同样的脚本。  


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

5. git cherry-pick 
    * 基本使用(将指定的提交--commit 应用于HEAD指向的commit)
```
1. 应用单个提交
git cherry-pick commit_A
cherry-pick拣选操作将提交commit_a (也可以填分支名(代表分支的最新提交), tag标签等)应用到HEAD指向的引用。

2. 应用多个提交
git cherry-pick commit_1 commit_4
应用两个提交commit_1, commit_4

git cherry-pick commit_1..commit_4
应用commit_1到commit_4的提交，包括commit_4,但不包括commit_1。如果需要包括commit_1，应该这样使用
git cherry-pick commit_1^..commit_4
```
    * 配置项
```
git cherry-pick命令的常用配置项如下:
-e，--edit                     // 打开外部编辑器，编辑提交信息
-n，--no-commit                // 只更新工作区和暂存区，不产生新的提交
-x                             // 在提交信息的末尾追加一行(cherry picked from commit ...)，方便以后查到这个提交是如何产生的
-s，--signoff                  // 在提交信息的末尾追加一行操作者的签名，表示是谁进行了这个操作
-m parent-number，--mainline parent-number // 如果原始提交是一个合并节点，来自于两个分支的合并，那么 Cherry pick 默认将失
                               // 失败，因为它不知道应该采用哪个分支的代码变动。-m配置项告诉 Git，应该采用哪个分支的变动。
                               // 它的参数parent-number是一个从1开始的整数，代表原始提交的父分支编号。
$ git cherry-pick -m 1 <commitHash>
上面命令表示，Cherry pick 采用提交commitHash来自编号1的父分支的变动。
一般来说，1号父分支是接受变动的分支（the branch being merged into），2号父分支是作为变动来源的分支（the branch being
merged from）。                              
```

    * 代码冲突
```
如果操作过程中发生代码冲突，Cherry pick 会停下来，让用户决定如何继续操作。
--continue
用户解决代码冲突后，第一步将修改的文件重新加入暂存区（git add .），第二步使用下面的命令，让 Cherry pick 过程继续执行。
$ git cherry-pick --continue

--abort                        // 发生代码冲突后，放弃合并，回到操作前的样子
--quit                         // 发生代码冲突后，退出 Cherry pick，但是不回到操作前的样子。
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
git diff 相比GNU diff命令更加强大，支持二进制文件差异等的扩展
a. 工作区与暂存区比较  git diff

b. 暂存区与HEAD比较  git diff --cached

c. 工作区与HEAD比较  git diff HEAD

d. 工作区与tag1比较  git diff tag1

e. 暂存区与tag1比较  git diff --cached tag1

f. 比较不同版本的差异 git diff <commit1> <commit2> -- <paths>

g. 非Git目录/文件的比较 git diff <path1> <path2>

h. 逐词比较，而非默认的逐行比较  git diff --word-diff
```

7. git stash
```
git stash save "save message"    保存当前的工作状态，并添加备注 (可能会慢慢被 git stash push替代)

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
9. git rebase
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




