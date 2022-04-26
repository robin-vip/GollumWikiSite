<h1> dd usage. </h1>

dd：用指定大小的块拷贝一个文件，并在拷贝的同时进行指定的转换。  
注意：指定数字的地方若以下列字符结尾，则乘以相应的数字：
```
c=1, w=2, b=512, kB=1000, k=1024, MB=1000*1000, M=1024*1024, xM=M
GB=1000*1000*1000, G=1024*1024*1024, and so on for T, P, E, Z, Y.
```
参数注释： 
``` 
1. if=文件名：输入文件名，缺省为标准输入。即指定源文件。< if=input file >
2. of=文件名：输出文件名，缺省为标准输出。即指定目的文件。< of=output file >
3. ibs=bytes：一次读入bytes个字节，即指定一个块大小为bytes个字节。
    obs=bytes：一次输出bytes个字节，即指定一个块大小为bytes个字节。
    bs=bytes：同时设置读入/输出的块大小为bytes个字节。
4. cbs=bytes：一次转换bytes个字节，即指定转换缓冲区大小。
5. skip=blocks：从输入文件开头跳过blocks个块后再开始复制。
6. seek=blocks：从输出文件开头跳过blocks个块后再开始复制。
注意：通常只用当输出文件是磁盘或磁带时才有效，即备份到磁盘或磁带时才有效。
7. count=blocks：仅拷贝blocks个块，块大小等于ibs指定的字节数。
8. conv=conversion：用指定的参数转换文件。
    ascii：转换ebcdic为ascii
    ebcdic：转换ascii为ebcdic
    ibm：转换ascii为alternate ebcdic
    block：把每一行转换为长度为cbs，不足部分用空格填充
    unblock：使每一行的长度都为cbs，不足部分用空格填充
    lcase：把大写字符转换为小写字符
    ucase：把小写字符转换为大写字符
    swab：交换输入的每对字节
    noerror：出错时不停止
    notrunc：不截短输出文件
    sync：将每个输入块填充到ibs个字节，不足部分用空（NUL）字符补齐。
9. iflag=flag 使用iflag来控制输入(读取数据)时的行为特征. oflag=flag 使用oflag来控制输出(写入数据)时的行为特征。
   flag 参数如下：
   append: 追加模式(仅对输出有意义；隐含了conv=notrunc)
   direct: 使用直接I/O 存取模式
   directory: 除非是目录，否则 directory 失败
   dsync: 使用同步I/O 存取模式
   sync: 同上，但是针对是元数据
   fullblock: 为输入积累完整块(iflag only)
   nonblack: 使用无阻塞I/O 存取模式
   noatime: 读写数据不更新访问时间
   noctty: -do not assign controlling terminal from file
   nofollow: -do not follow symlinks
```