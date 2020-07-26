<h1> taglist install usage. </h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)  

# Install taglist
1. 下载 **[taglist_46.zip](https://www.vim.org/scripts/download_script.php?src_id=19574)**  

2. 安装 taglist
```
将doc/taglist.txt, plugin/taglist.vim分别拷贝到~/.vim/doc/和~/.vim/plugin/目录
```

# taglist usage
1. taglis快捷方式
```
<CR>          跳到光标下tag所定义的位置，用鼠标双击此tag功能也一样
o             在一个新打开的窗口中显示光标下tag
<Space>       显示光标下tag的原型定义
u             更新taglist窗口中的tag
s             更改排序方式，在按名字排序和按出现顺序排序间切换
x             taglist窗口放大和缩小，方便查看较长的tag
-             将tag折叠起来，同zc
*             打开所有的折叠，同zR
=             将所有tag折叠起来，同zM
[[            跳到前一个文件
]]            跳到后一个文件
q             关闭taglist窗口
<F1>          显示帮助
```

2. taglist常用配置选项
```
Tlist_Ctags_Cmd: 用于指定你的Exuberant ctags程序的位置，如果它没在你PATH变量所定义的路径中，需要使用此选项设置一下；
Tlist_Show_One_File: 设置为1只显示一个文件的tag, 缺省为 显示多个文件的tag;
Tlist_Use_Right_Window: 设置为1taglist窗口出现在右侧,缺省显示在左侧;
在gvim中，如果你想显示taglist菜单，设置Tlist_Show_Menu为１。你可以使用Tlist_Max_Submenu_Items和Tlist_Max_Tag_Length来控制菜单条目数和所显示tag名字的长度；
Tlist_Use_SingleClick: 设置为1单击tag就跳转, 缺省是在双击一个tag时，才会跳到该tag定义的位置;
Tlist_Auto_Open: 设置为1, 启动VIM后，自动打开taglist窗口;
Tlist_Close_On_Select: 设置为1, 选择了tag后自动关闭taglist窗口;
Tlist_File_Fold_Auto_Close: 设置为1, 当同时显示多个文件中的tag时, 可使taglist只显示当前文件tag，其它文件的tag都被折叠起来;
Tlist_GainFocus_On_ToggleOpen: 设置为1, 在使用:TlistToggle打开taglist窗口时，输入焦点在taglist窗口中;
Tlist_Process_File_Always: 设置为1, taglist始终解析文件中的tag，不管taglist窗口有没有打开;
Tlist_WinHeight和Tlist_WinWidth可以设置taglist窗口的高度和宽度。Tlist_Use_Horiz_Window为１设置taglist窗口横向显示；
```


