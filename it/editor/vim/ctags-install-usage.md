<h1> ctags install usage. </h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)  

# Install ctags  

```
# sudo apt-get install exuberant-ctags
```

# ctags usage
1. 生成ctags文件
```
在源文件目录下执行命令
# ctags  -R --file-scope=yes --langmap=c:+.h --languages=c,c++ --links=yes --c-kinds=+px --c++-kinds=+px --fields=+iafksS --extra=+qf
会生成一个tags文件，里面包含了所有源文件的符号信息。在vim中，快捷键ctrl+］会跳到当前变量或函数的定义处。
--file-scope： 指示是否仅在单个文件范围内的标签应包含在输出中。
--links: 是否需要遵循符号链接。
--langmap=语言:+后缀（要加.） 为已知语言添加扩展名
--{language}-kinds：这是通用格式。 c++-kinds 用于指定C++语言的 tags记录类型, --c-kinds用于指定c语言的。  
--fields=+iafksS: 为标签添加继承信息(inheritance)，访问控制(access)信息，函数特征(function Signature,如参数表或原型等),使能文件范围限制(file-restricted)，标签种类为单个字母(Kind of tag as a single letter)，使能标签定义范围(Scope of tag definition)，函数特征(function Signature,如参数表或原型等)
--extra: 这个选项用于增加额外的条目: f表示为每个文件增加一个条目，  q为每个类增加一个条目
```

2. 修改vim配置文件，使其自动生成tags文件
```
# vi ~/.vimrc
function! UpdateCtags()
    let curdir=getcwd()
    while !filereadable("./tags")
        cd ..
        if getcwd() == "/"
            break
        endif
    endwhile
    if filewritable("./tags")
        !ctags -R --file-scope=yes  --c-kinds=+px --c++-kinds=+px --fields=+iafksS --extra=+qf
        TlistUpdate
    endif
    execute ":cd " . curdir
endfunction

nmap <F7> :call UpdateCtags() <CR>
```
添加F7映射键

3. ctags跳转  
    3.1 显示多个匹配
```
g+Ctrl+]: 显示多个匹配项，并用数字表示。输入数字并回车就可以跳转到相应的匹配处。
```
    3.2 多个匹配处的跳转
```
:tfirst     或:tf           到第一个匹配
:tlast      或:tl           到最后一个匹配
:tnext      或:tn           到下一个匹配
:tprevious  或:tp           到前一个匹配
:[count]tnext               向后[count]个匹配
:[count]tprevious           向前[count]个匹配
```

# Notes：
1. 源码目录最好用全局变量
```
# ctags -f ctags_file src_code_full_path
源码目录用全局路径生成的tags file可以拷贝到任意路径
```


