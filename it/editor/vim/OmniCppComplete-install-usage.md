<h1> OmniCppComplete install usage. </h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)  

# Install
1. 下载 **[omnicppcomplete-0.41.zip](https://www.vim.org/scripts/download_script.php?src_id=7722)**

2. 安装
```
将doc/omnicppcomplete.txt拷贝到~/.vim/doc目录；
将after, autoload目录拷贝到~/.vim目录
```

# Usage
配置vimrc
```
# vi ~/.vimrc
添加一下内容
" OmniCppComplete
set completeopt=menu,longest,menuone
let OmniCpp_NamespaceSearch = 2
let OmniCpp_GlobalScopeSearch = 1
let OmniCpp_ShowAccess = 1
let OmniCpp_ShowPrototypeInAbbr = 1 
let OmniCpp_MayCompleteDot = 1   
let OmniCpp_MayCompleteArrow = 1 
let OmniCpp_MayCompleteScope = 1 
let OmniCpp_DefaultNamespaces = ["std", "_GLIBCXX_STD"]
let OmniCpp_SelectFirstItem = 2
let OmniCpp_DisplayMode=1

au CursorMovedI,InsertLeave * if pumvisible() == 0|silent! pclose|endif
```