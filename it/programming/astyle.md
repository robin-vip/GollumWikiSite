# astyle

## astyle 参数说明
* --style= 支持以下预定义风格和缩进:
```
ansi: ANSI 风格格式和缩进；  or -A1
jave: Java 风格格式和缩进;   or -A2
kr: Kernighan&Ritchie 风格格式和缩进;  or -A3
gnu: GNU 风格格式和缩进;     or -A7
linux: Linux 风格格式和缩进; or -A8
```
* --indent=  缺省4个空格的缩进，也可以通过这个参数设置以下参数：
```
--indent=spaces=# OR -s# 指定缩进的空格个数
--indent=tab OR --indent=tab=# OR -t OR -t#  用tab作为缩进，并指定tab占的空格数
```
* -n 不生成备份文件，即默认的 .orig文件;
* -j 给每个"if", "for", "while"增加大括号;
* -M 对定义的参数和变量进行对齐;
* -w 对宏进行对齐处理;
* -f 在两行不相关的代码之间插入空行，如import和public class之间、public class和成员之间等；
* -F 空行分隔无关块;
* -S switch 与 case 不同列, case缩进;
* -N 表示命名空间namespace内的缩进;
* -k1 *和&在表示指针和引用类型时, 和类型名称并紧, 和变量名之间留空格;
* -U 移除括号两边不必要的空格 (如：MessageBox.Show ( "aaa" ), 处理后变成MessageBox.Show("aaa"));
* -H "if", "for", "while" 等关键字右边增加一个空格;
* -p 在操作符两边插入空格，如=、+、-等;
* -P 在括号两边插入空格。另，-d只在括号外面插入空格，-D只在里面插入;-
* -c 将Tab替换为空格;
* -x 删除函数或者方法内的空行;
* -r OR -R 在子目录下递归处理;
* --exclude=####  排除指定的文件和目录;
* -a 大括号保留在上一行;
* -v 输出详细处理信息;

## 外部链接
[astyle使用说明](https://www.cnblogs.com/jiangxinnju/p/4908575.html)  
[astyle编程语言格式化工具的中文说明](https://www.cnblogs.com/RioTian/p/14771895.html)





