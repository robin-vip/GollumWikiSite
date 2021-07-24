<h1>Git diff</h1>

```
git diff 相比GNU diff命令更加强大，支持二进制文件差异等的扩展
1. 工作区与暂存区比较  git diff

2. 暂存区与HEAD比较  git diff --cached

3. 工作区与HEAD比较  git diff HEAD

4. 工作区与tag1比较  git diff tag1

5. 暂存区与tag1比较  git diff --cached tag1

6. 比较不同版本的差异 git diff <commit1> <commit2> -- <paths>   // "--" 和 “<paths>”之间是有空格的

7. 非Git目录/文件的比较 git diff <path1> <path2>

8. 逐词比较，而非默认的逐行比较  git diff --word-diff

9. 比较不同版本commit修改的文件列表 git diff <commit1> <commit2> --name-only

10. 比较不同版本commit修改的文件列表以及文件修改的状态 git diff <commit1> <commit2> --name-status
```