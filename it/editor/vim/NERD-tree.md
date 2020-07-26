<h1> NERD_tree install usage. </h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)  

NERD_tree包含在Trinity插件下载包中。NERD_tree实现文件树功能，trinity.vim是实现taglist, SrcExpl和NERD_tree三个功能框快速开关的功能。

1. 下载 **[Trinity-2.1.zip](https://www.vim.org/scripts/download_script.php?src_id=19683)**

2. 安装 
a. NERD_tree
```
将NERD_tree.vim拷贝到~/.vim/plugin/目录
```
b. trinity
```
将trinity.vim拷贝到~/.vim/plugin/目录
```

3. 设置映射键通过trinity管理taglist, SrcExpl和NERD_tree的打开和关闭
```
在～/.vimrc中添加下面的内容
" Open and close all the three plugins on the same time
nmap <F8>   :TrinityToggleAll<CR> 
" Open and close the srcexpl.vim separately 
nmap <F9>   :TrinityToggleSourceExplorer<CR> 
" Open and close the taglist.vim separately 
nmap <F10>  :TrinityToggleTagList<CR>
" Open and close the NERD_tree.vim separately 
nmap <F11>  :TrinityToggleNERDTree<CR>

```

