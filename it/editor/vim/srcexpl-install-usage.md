<h1> srcexpl install usage. </h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)  

1. 下载 **[SrcExpl-5.1.zip](https://www.vim.org/scripts/download_script.php?src_id=20807)**

2. 安装
```
将doc/srcexpl.txt, plugin/srcexpl.vim分别拷贝到~/.vim/doc/和~/.vim/plugin/目录
```

3. 修改插件
```
# vi ~/.vim/plugin/srcexpl.vim
将“exe "set tags=tags;"”注释掉，否则打开srcexpl是会调用SrcExpl_Init函数将vimrc设置的tags变量值覆盖掉。

# vi ~/.vimrc
let g:SrcExpl_winHeight = 8
let g:SrcExpl_refreshTime = 100 "ms
let g:SrcExpl_jumpKey = "<ENTER>"
let g:SrcExpl_gobackKey = "<SPACE>"
" // Do not let the Source Explorer update the tags file when opening
let g:SrcExpl_isUpdateTags = 0

" // Set 100 ms for refreshing the Source Explorer 
let g:SrcExpl_refreshTime = 100 

" // In order to avoid conflicts, the Source Explorer should know what plugins except
" // itself are using buffers. And you need add their buffer names into below listchars" // according to the command ":buffers!"
let g:SrcExpl_pluginList = [
        \ "__Tag_List__",
        \ "_NERD_tree_",
        \ "Source_Explorer"
    \ ]
```
