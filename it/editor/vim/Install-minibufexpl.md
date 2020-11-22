<h1> minibufexpl install usage. </h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)  

# Install minibufexpl  
1. 下载 **[minibufexpl.vim](https://www.vim.org/scripts/download_script.php?src_id=3640)**

2. 安装  
```
将minibufexpl.vim拷贝到~/.vim/plugin/目录
```

3. 设置
在vimrc文件中天添加如下内容
```
" ......................................................................................
" Settings for vim buffer plugin minibufexpl.
" ......................................................................................
let g:miniBufExplMapCTabSwitchBufs = 1
let g:miniBufExplMapWindowNavVim = 1
let g:miniBufExplModSelTarget = 1
```






