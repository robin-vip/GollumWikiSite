<h1> NerdCommenter install usage. </h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)  
代码注释插件

# Install
1. 下载 **[NERD_commenter.zip](https://www.vim.org/scripts/download_script.php?src_id=14455)**

2. 安装
```
将plugin/NERD_commenter.vim, doc/NERD_commenter.txt分别拷贝到~/.vim/plugin和~/.vim/doc目录
```

# Usage
1. 配置~/.vimrc
```
let g:NERDSpaceDelims=1                                      // 注释符号后面空一格
```

2. 注释
```
:h NERDCommenter                                             // 使用帮助
,ca： 在可选的注释方式之间切换，比如C/C++ 的块注释/* */和行注释//
,cc: 注释当前行
,c: 切换注释/非注释状态
,cs: 以”性感”的方式注释
,cA: 在当前行尾添加注释符，并进入Insert模式
,cu: 取消注释
Normal模式下，几乎所有命令前面都可以指定行数。  比如  输入  6,cs    的意思就是以性感方式注释光标所在行开始6行代码
Visual模式下执行命令，会对选中的特定区块进行注释/反注释

其它的nerdcommenter命令可以在NORMAL模式下输入命令 :map 看到
```

3. 注意
```
需要在vim配置文件中文件类型检查打开，否则使用注释命令时会有如下提示：
NERDCommenter:filetype plugins should be enabled. See :help NERDComInstallation and :help :filetype-plugin-on

在vim 配置文件中添加如下：
if has("autocmd")
  filetype plugin on
endif
```

