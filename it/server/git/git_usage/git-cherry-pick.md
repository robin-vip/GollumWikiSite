<h1>Git cherry pick</h1>

* **基本使用(将指定的提交--commit 应用于HEAD指向的commit)**
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

* **配置项**
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

* **代码冲突**
```
如果操作过程中发生代码冲突，Cherry pick 会停下来，让用户决定如何继续操作。
--continue
用户解决代码冲突后，第一步将修改的文件重新加入暂存区（git add .），第二步使用下面的命令，让 Cherry pick 过程继续执行。
$ git cherry-pick --continue

--abort                        // 发生代码冲突后，放弃合并，回到操作前的样子
--quit                         // 发生代码冲突后，退出 Cherry pick，但是不回到操作前的样子。
```