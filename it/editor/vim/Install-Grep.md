<h1> Grep install usage. </h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)  

# Install Grep
1. 下载 [grep.zip](https://www.vim.org/scripts/download_script.php?src_id=25998)

2. 安装
```
将解压后的autoload, doc, plugin目录下的文件分别拷贝到~/.vim/autoload, ~/.vim/doc, ~/.vim/plugin目录下
```

# Grep usage
1. 命令说明
```
:Grep	                      按照指定的规则在指定的文件中查找
:Rgrep	                      同上, 但是是递归的grep
:GrepBuffer	              在所有打开的缓冲区中查找
:Bgrep	                      同上
:GrepArgs	              在vim的argument filenames (:args)中查找
:Fgrep	                      运行fgrep
:Rfgrep	                      运行递归的fgrep
:Egrep	                      运行egrep
:Regrep	                      运行递归的egrep
:Agrep	                      运行agrep
:Ragrep	                      运行递归的agrep
```