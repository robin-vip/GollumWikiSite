<h1>Linux terminal shortcut</h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)

1. 复制,粘贴
```
复制: ctrl-shift-c
粘贴: ctrl-shift-v
```
2. 窗口操作
```
新建窗口: Shift+Ctrl+N
关闭终端: Shift+Ctrl+Q

新建标签页: Shift+Ctrl+T
关闭标签页: Shift+Ctrl+W
前一标签页: Ctrl+PageUp
后一标签页: Ctrl+PageDown
标签页左移: Shift+Ctrl+PageUp
标签页右移: Shift+Ctrl+PageDown
切换到标签页1: Alt+1
切换到标签页2: Alt+2
切换到标签页3: Alt+3
```

3. 改变终端大小
```
全屏: F11
放大: Ctrl+Shift+'='
减少: Ctrl+'-'
缺省大小: Ctrl+0
```

4. shell快捷键
```
命令补全: Tab

清屏: Ctrl+l

杀死当前任务: Ctrl+c

历史命令：
显示历史命令列表: history
显示上一条命令: Ctrl+p
显示下一条命令: Ctrl+n
执行历史命令列表的第num条命令: !num
执行含有string字符串的最新命令: !?string?

历史命令匹配搜索: 
Ctrl+r 然后输入若干字符，开始向上搜索包含该字符的命令，继续按Ctrl+r，搜索上一条匹配的命令Ctrl+s 
第一条历史命令: Alt+<
最后一条历史命令: Alt+>

移动命令行上的光标
光标向前移动一个字符: Ctrl+f
光标向后移动一个字符: Ctrl+b
光标向前移动一个单词: Alt+f
光标向后移动一个单词: Alt+b
光标移动到当前命令行的开头: Ctrl+a
光标移动到当前命令行的结尾: Ctrl+e
光标移动到当前单词的开头: Esc+b
光标移动到当前单词的结尾: Esc+f

命令行上剪切，删除：
剪切命令行开始位置到当前位置（光标，不包括自身）的内容: Ctrl+u
剪切命令行当前位置到结束位置（光标，包括自身）的内容: Ctrl+k
剪切光标所在处之前的一个单词（以空格、标点等为分隔符）: Ctrl+w
剪切光标之后的一个单词: Alt+d      //(当前系统自带终端测试可以，但在secureCRT不行，应该是特殊键映射的关系)

粘贴剪切内容: Ctrl+y

删除光标所在处字符: Ctrl+d
删除光标所在处前一个字符: Ctrl+h

交换位置：
交换光标所在处及其之前的字符位置(并将光标移动到下一个字符): Ctrl+t
交换当前与以前单词的位置: Esc+t
交换光标所在处及其相邻单词的位置: Esc+t


大小写转换
把当前词转化为大写: Alt+u
把当前词转化为小写: Alt+l
把当前词汇变成首字符大写（光标要停在首字母上）: Alt+c

插入特殊字符: Ctrl+v   (Ctrl+v+Tab加入Tab字符键)  

撤销刚才的操作： Ctrl+(x u) 按住Ctrl的同时再先后按x和u

上一条命令的参数"!$": ls !$   // 执行命令ls，并以上一条命令的参数为其参数

挂起当前shell: Ctrl+s
退出挂起状态: Ctrl+q
```
