# sed usage

## 1. sed 命令说明
sed 分析Standard Input（stdin）的数据，然后将数据经过处理后输出到standard out (stdout)。 处理包括行取代，删除，新增，提取特定行等功能。

## 2. 命令格式和参数说明
* sed [-nefr] [动作]
```
参数:
-n   : 	使用安静(silent)模式。 默认情况下，sed 会将所有来自STDIN的数据（处理后）输出到STDOUT。但如果加上`-n`参数后则不会
        再输出到STDOUT。
-e   :  直接在指令列模式上进行sed的动作编辑；
-f   :  可在sed命令之前将sed 动作写到文档中， -f filename 则可以执行 filename 内的sed 动作；
-r   :  支持延伸型正规标识符的语法。 （缺省是基础正规表示法语法）
-i   :  直接修改源文件；

动作说明： [n1[,n2]]function
n1, n2 : 行数范围是可选的，不是必须存在的。如果动作的范围是 5 到 30 行之间进行，则 5,30function。如果是5到最后一行，则
         5function

function:
a    :  新增， a的后面可以接字符串，而这些字符串会在新的一样出现(目前的下一行)；
c    :  取代， c的后面可以接字符串，而这些字符串可以取代n1,n2之间的行；
d    :  删除， 后面不需要接其它参数；
i    ： 插入， i的后面可以接字符串，而这些字符串会在新的一行出现（当前的上一行）;
p    :  打印， 将某个选择的数据输出。通常p 会与参数 sed -n 一起运作；
s    :  取代， 可以直接进行取代的工作。通常这个s 的动作可以搭配正规表示法。 例如: 5,30s/old/new/g
```

## 3. 使用范例
* 文件字符串替换并写回源文件
```
1. 修改指定目录及子目录下所有匹配的文件
find . -type f | xargs sed -i "s/old/new/g"
或者
find . -type f -exec sed  -i "s/old/new/g" {} \;

注意点：
遍历目录下的所有文件： find . -type f 
如果需要修改的文件名有规律， 可以通过 find . -type f -name "xxx"缩小范围，节省命令处理的时间
sed替换之后，写回源文件： sed -i 选项

2. 修改指定文件
sed -i "s/old/new/g" filename
```

