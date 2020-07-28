<h1> OmniCppComplete install usage. </h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)  
代码自动补全，配合autocomplpop插件

# Install
1. 下载 **[omnicppcomplete-0.41.zip](https://www.vim.org/scripts/download_script.php?src_id=7722)**

2. 安装
```
将doc/omnicppcomplete.txt拷贝到~/.vim/doc目录；
将after, autoload目录拷贝到~/.vim目录
```

# Usage
1. 配置vimrc
```
# vi ~/.vimrc
添加一下内容
" OmniCppComplete
set completeopt=menu,longest,menuone                          // 关掉智能补全时的预览窗口
let OmniCpp_NamespaceSearch = 2                               // search namespaces in this and included files
let OmniCpp_GlobalScopeSearch = 1                             // enable the global scope search
let OmniCpp_ShowAccess = 1
let OmniCpp_ShowPrototypeInAbbr = 1                           // show function prototype in popup window
let OmniCpp_MayCompleteDot = 1                                // autocomplete with .
let OmniCpp_MayCompleteArrow = 1                              // autocomplete with ->
let OmniCpp_MayCompleteScope = 1                              // autocomplete with ::
let OmniCpp_DefaultNamespaces = ["std", "_GLIBCXX_STD"]
let OmniCpp_SelectFirstItem = 2                               // select first item (but don't insert)
let OmniCpp_DisplayMode=1                                     // Class scope completion mode: always show all members

au CursorMovedI,InsertLeave * if pumvisible() == 0|silent! pclose|endif
```

2. 快捷方式
```
注意：在自动补全的点，Vim必须知道可能补全的定义。比如说，在namespace std命名空间下的变量和函数，必须要用using namespace std;暴露出来，否则是不能补全的。
当自动补全下拉窗口弹出后，一些可用的快捷键:
Ctrl+P  向前切换成员
Ctrl+N  向后切换成员
Ctrl+E  表示退出下拉窗口, 并退回到原来录入的文字
Ctrl+Y  表示退出下拉窗口, 并接受当前选项
其他补全方式:
Ctrl+X Ctrl+L 整行补全
Ctrl+X Ctrl+N  根据当前文件里关键字补全
Ctrl+X Ctrl+K  根据字典补全
Ctrl+X Ctrl+T  根据同义词字典补全
Ctrl+X Ctrl+I  根据头文件内关键字补全
Ctrl+X Ctrl+]  根据标签补全
Ctrl+X Ctrl+F  补全文件名
Ctrl+X Ctrl+D  补全宏定义
Ctrl+X Ctrl+V  补全vim命令
Ctrl+X Ctrl+U  用户自定义补全方式
Ctrl+X Ctrl+S  拼写建议
帮助文档
:help omnicppcomplete
```