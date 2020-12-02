<h1> VisualMark install usage. </h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)  

# Featrue
* 优点
```
相比vim自带的可以标记可视书签 （被标签的行高亮显示）
```
* 缺点
```
1. 书签不能自动保存, 关闭vim就没了
2. 切换书签时不能在不同文件间切换, 只能在同一个文件中切换
```

# Install VisualMark
1. 下载 [visualmark.vim](https://www.vim.org/scripts/download_script.php?src_id=4700)

2. 安装  
```
将visualmark.vim 拷贝到~/.vim/plugin目录下
```

# Usage
1. mm 标记或删除书签

2. F2 正向跳转书签

3. 修改高亮颜色
修改 visualmark.vim文件
```
if &bg == "dark"
 highlight SignColor ctermfg=white ctermbg=blue guifg=white guibg=RoyalBlue3
else
 highlight SignColor ctermbg=yellow ctermfg=blue guibg=grey guifg=RoyalBlue3
endif
```

4. 解决mm标记 E197错误  
在ubuntu 标记时提示：E197: Cannot set language to "en_US"  
修改 visualmark.vim文件, 将 
```
  exec ":lan mes en_US"
```
改成
```
  if has("win32") || has("win95") || has("win64") || has("win16")
      exec ":lan mes en_US"
  else
      exec ":lan POSIX"
  endif
```
