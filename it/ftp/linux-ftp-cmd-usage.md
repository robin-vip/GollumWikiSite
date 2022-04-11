# linux ftp cmd usage

1. 登录ftp服务器
```
ftp [IP] [PORT]                               // 登陆ftp服务器，本机登陆可以不写IP
```

2. 查看ftp中的文件列表（ls和dir都可以查看）

3. 切换ftp的目录 cd

4. 查询系统中的文件列表
```
! [linux系统命令]                              // 在ftp服务器中执行系统命令，之后回到ftp环境中
```

5. 切换linux中的工作目录 lcd 

6. 创建和删除ftp目录
```
mkdir dir_name
rmdir dir_name
```

7. 下载单个文件
```
get file_name [new_file_name]             // 下载后重命名为new_file_name， 这个参数是可选的
```

8. 下载多个文件
```
mget file_name1 file_name2
```

9. 上传单个文件
```
put file_name [new_file_name]             // 上传后重命名为new_file_name， 这个参数是可选的
```

10. 上传多个文件
```
mput file_name1 file_name2
```

11. 修改ftp文件名
```
rename file_name new_file_name
```

12. 删除ftp文件
```
delete file_name
```

13. 删除多个ftp文件
```
mdelete file_name1 file_name2
```

14. 删除ftp目录
```
rmdir dir_name
```

15. 切换传输模式
```
ascii                                     // 切换为ascii模式
bin                                       // 切换为二进制模式，默认登陆就是二进制传输模式
```

16. 关闭和重连ftp  close, 
```
close
open [IP] [PORT]                               // 登陆ftp服务器，本机登陆可以不写IP
```

17. 退出ftp会话
```
quit
```







