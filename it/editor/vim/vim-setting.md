<h1> vim setting. </h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)  

1. 重新打开文件时跳转到上次退出时所在行位置
```
根据下面的注释，修改～/.vimrc文件（将注释符去掉使能这个功能）

" Uncomment the following to have Vim jump to the last position when                        
" reopening a file                                                                          
if has("autocmd")                                                                           
  au BufReadPost * if line("'\"") > 1 && line("'\"") <= line("$") | exe "normal! g'\"" | endif
endif

```