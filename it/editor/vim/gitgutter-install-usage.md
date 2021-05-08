<h1> gitgutter install usage. </h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)  
Vim插件用于在符号标记列中显示git diff的结果

# Install
1. 下载 **[vim-gitgutte.zip](https://github.com/airblade/vim-gitgutter/archive/refs/heads/master.zip)**

2. 安装
```
将autoload, plugin和doc目录下的文件分别拷贝到~/.vim/autoload, ~/.vim/plugin和~/.vim/doc目录
```

# Vimrc settings
1. 设置标记列的颜色 （缺省的可能会导致标记不可见）
```
highlight SignColumn guibg=black ctermbg=black
highlight GitGutterAdd    guifg=#009900 ctermfg=2
highlight GitGutterChange guifg=#bbbb00 ctermfg=3
highlight GitGutterDelete guifg=#ff2222 ctermfg=1
```

2. 映射
```
nmap ghs <Plug>(GitGutterStageHunk)
nmap ghu <Plug>(GitGutterUndoHunk)
nmap ghp <Plug>(GitGutterPreviewHunk)
```

3. 设置状态栏
```
function! GitStatus()
  let [a,m,r] = GitGutterGetHunkSummary()
  return printf('+%d ~%d -%d', a, m, r)
endfunction
set statusline+=%{GitStatus()}
```

# Usage
1. 块(hunk)跳转  
`[c  跳转下一个hunk`
`]c  跳转上一个hunk`

2. 预览修改  
`<leader>hp  光标必须在hunk中`  
`<leader> 在我的vim设置中是逗号`

3. 暂存修改  
`<leader>hs  光标必须在hunk中`

4. 撤销修改  
`<leader>hu  光标必须在hunk中`

5. 关闭gitgutter （缺省是打开的）  
`:GitGutterBufferDisable`  
`:GitGutterBufferEnable  是打开gitgutter`

