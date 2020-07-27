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
```
