<h1>Git diff</h1>

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