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

2. 窗口方向键映射
```
nmap <C-J> <C-W>j              // 向上的窗口
nmap <C-K> <C-W>k              // 向下的窗口
nmap <C-H> <C-W>h              // 向左的窗口
nmap <C-L> <C-W>l              // 向右的窗口
```

3. 指定一行的最大字符数
```
set tw=78                      // 一行的最大字符数是78，set tw=0取消限制  tw也可以是textwidth
```

4. 高亮指定的列
```
set cc=90                     // 将第90列高亮显示， set cc=0 取消高亮显示

设置函数映射，通过按下,ch 就可以将当前光标下的列高亮，再按下一次，取消高亮；并且可以同时多列高亮。
map ,ch :call SetColorColumn()<CR>
function! SetColorColumn()
    let col_num = virtcol(".")
    let cc_list = split(&cc, ',')
    if count(cc_list, string(col_num)) <= 0
        execute "set cc+=".col_num
    else
        execute "set cc-=".col_num
    endif
endfunction

```

5. 设置光标所在行线
```
set cul                      // 光标所在行下方会有一条横线， set nocul 取消这条横线
```

