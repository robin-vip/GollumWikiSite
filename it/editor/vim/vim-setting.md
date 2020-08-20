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

# 个人vimrc设置
```
"set showcmd        " Show (partial) command in status line. 在vim状态行显示部分命令
set showmatch       " Show matching brackets.    显示匹配的括号
set ignorecase      " Do case insensitive matching  搜索模式忽略大小写 （也可写作"set ic", 取消是"set noic"）
set smartcase       " Do smart case matching   如果搜索模式包含大写字符，不使用 'ignorecase' 选项。只有在输入搜索模式并且打开 'ignorecase' 选项时才会使用。
set incsearch       " Incremental search   增量搜索（输入字符串就显示匹配点）
"set hlsearch        " highlight all matches of the most recent search pattern. 高亮所有的匹配点
"set autowrite      " Automatically save before commands like :next and :make   自动把内容写回文件: 如果文件被修改过，在每个 :next、:make之前
"set hidden     " Hide buffers when they are abandoned
"set mouse=a        " Enable mouse usage (all modes)   使用鼠标
set number          " show line number  显示行号，也可以用"set nu", 取消用"set nonu"

set tabstop=4       " Replace TAB with 4 backspace. 修改Tab键显示的宽度（4个空格，默认是8个），也可以用“set ts=4”
set expandtab       " 选项把插入的Tab字符替换成特定数目的空格，具体空格数据与tabstop选项值有关。 如果想插入Tab键（如makefile文件中），可以先按ctrl+v，再按Tab键。

set laststatus=2    “ 是否显示状态栏。0 表示不显示，1 表示只在多窗口时显示，2 表示显示。

" set auto indent.
set shiftwidth=4    " (自动) 缩进使用的4个空格
set autoindent      " 设置自动对齐(缩进)：即每行的缩进值与上一行相等；使用 noautoindent 取消设置
set cindent         " 使用 C/C++ 语言的自动缩进方式
"set smartindent    " 每一行都和前一行有相同的缩进量，同时这种缩进形式能正确的识别出花括号，当遇到右花括号（}），则取消缩进形式。此外还增加了识别C语言关键字的功能。如果一行是以#开头的，那么这种格式将会被特殊对待而不采用缩进格式。

" set formatoptions=tcqro  " 确定与文本格式化有关的基本选项。缺省值是“tcq”，常用的数值有： （可以通过:help fo-table 查看）
" t: 根据 textwidth 自动折行;
" c：在（程序源代码中的）注释中自动折行，插入合适的注释起始字符；
" r：插入模式下在注释中键入回车时，插入合适的注释起始字符；
" q：允许使用“gq”命令对注释进行格式化；
" n：识别编号列表，编号行的下一行的缩进由数字后的空白决定（与“2”冲突，需要“autoindent”）；
" 2：使用一段的第二行的缩进来格式化文本；
" l：在当前行长度超过 textwidth 时，不自动重新格式化；
" m：在多字节字符处可以折行，对中文特别有效（否则只在空白字符处折行）；
" M：在拼接两行时（重新格式化，或者是手工使用“J”命令），如果前一行的结尾或后一行的开头是多字节字符，则不插入空格，非常适合中文

" Highlight the current line.
" set cursorline     " 高亮显示当前行（有下划线）， "set nocursorline"取消

" Fold settings.
" manual method settings.
set foldmethod=syntax  ” 设置折叠方法，默认是manual，indent（常用）缩进折叠方法，相同的缩进中代码会被折叠。syntax （不常用）语法高亮折叠，在c/c++中会折叠花括号部分，其它格式代码中有的不能自动折叠。 marker （常用）标记折叠方法，如上面1-6所使用的方法。关闭vim折叠信息不会丢失，而且易用控制和标注。还有两种 diff 和 expr。
set foldcolumn=3     " the number of fold status column.   设置折叠栏的宽度为3个字符

set foldlevel=99     " 打开所有折叠，设置foldlevel为最高级别。关闭所有折叠，设置foldlevel为0
set foldminlines=8
set foldenable

"set textwidth=120 " the max number of showing characters in a line.  设置一行的最大字符数，超过会自动换行
set cc=90

"set wrap            " 自动折行，即太长的行分成几行显示 "set nowrap"关闭自动折行

"set linebreak       " 只有遇到指定的符号（比如空格、连词号和其他标点符号），才发生折行。也就是说，不会在单词内部折行。

set undofile        " save the hisotry of editting   保留撤销历史  Vim 会在编辑时保存操作历史，用来供用户撤消更改。默认情况下，操作记录只在本次编辑时有效，一旦编辑结束、文件关闭，操作历史就消失了。打开这个设置，可以在文件关闭后，操作记录保留在一个文件里面，继续存在。这意味着，重新打开一个文件，可以撤销上一次编辑时的操作。
" set file path for backup, undo.
set backupdir=~/.vim/.backup//     " 设置备份文件的路径，修改文件未保存之前保存一份未修改的版本
set directory=~/.vim/.swp//        " 交换文件路径
set undodir=~/.vim/.undo//         " 撤销文件路径

set autochdir       " 自动切换工作目录  一个 Vim 会话之中打开多个文件的情况，默认的工作目录是打开的第一个文件的目录。该配置可以将工作目录自动切换到，正在编辑的文件的目录。

set visualbell      " 出错时，发出视觉提示，通常是屏幕闪烁

set history=1000    " 设置vim 历史命令的数量


set autoread        " 当文件在外部被改变时，vim自动更新载入

"set listchars=tab:»■,trail:■  " TAB会被显示成 "»■" 而行尾多余的空白字符显示成 "■" 
"set list           " 将Tab键显示出来， TAB 键显示为 ^I，而 $显示在每行的结尾，以便你能找到可能会被你忽略的空白字符在哪里

set wildmenu        " 使用'wildmenu'选项，将启用增强模式的命令行补全。在命令行中输入命令时，按下'wildchar'键（默认为Tab）将自动补全命令和参数：此时将在命令行的上方显示可能的匹配项；继续按下'wildchar'键，可以遍历所有的匹配项；也可以使用方向键或者CTRL-P/CTRL-N键，在匹配列表中进行移动；最后点击回车键，选择需要的匹配项。
set wildmode=longest:list,full  " 命令自动补全模式  使用"longest:list,full"选项，点击Tab键，将显示可能匹配的文件列表，并使用最长的子串进行补全；再次点击Tab键，可以在wildmenu中遍历匹配的文件列表：

" QuickFix setting
map <F3> :make clean<CR><CR><CR>   " 按下F3，执行make clean
map <F6> :make<CR><CR><CR> :copen<CR><CR>    " 按下F6，执行make编译程序，并打开quickfix窗口，显示编译信息
map <F5> :cp<CR>    " 按下F5，光标移到上一个错误所在的行
map <F4> :cn<CR>    " 按下F4，光标移到下一个错误所在的行
```
