<h1>Install smaba service</h1>
操作系统：Ubuntu 20.04 LTS


1. 安装samba服务
```
$ sudo apt-get install samba
```

2. 给samba服务添加用户 （必须是linux系统中的用户）
```
$ sudo smbpasswd -a user1                   // 添加用户user1并设置samba密码
```

3. smaba设置（配置smb.conf文件）
```
$ cd /etc/samba
$ sudo cp smb.conf smb.conf_bak                 // 修改前备份
$ sudo vi smb.conf

[x3] //方框号中的x3这个名字可以随便取，只是在win的网上邻居中显示的共享文件夹名

path=/home/x4 //x4为你要共享的文件夹名，在共享前还要建立这个文件夹，并设好权限以便访问，下面会说明。

valid users=user1 //这个x4共享目录只允许user1这个用户进入
; browseable = yes  // ';'是将这一行注释，这个表示在window下是否可见
writable=yes　　 //允许user1在x4目录中进行读和写操作，反之no
```

4. 建立共享目录
```
$ sudo mkdir /home/x4
$ sudo chown -R user1:user1 /home/x4 //因为是root建立的目录，其它用户只有读的权限，所还得把权限改一下。当然也可以简单的用#chmod 777 /home/x4。还有个问题就是共享里目录的文件如果有些能访问有些不能访问，那肯定也是权限的问题,进入/home/x4,直接#chmod 777 *来解决。
```

5. 重启samba服务
```
$ sudo /etc/init.d/smbd restart
```

6. 安装图形配置界面 （可选）
```
$ sudo apt-get install system-config-samba
（最好选择http://mirrors.163.com 源，下载速度更快）
安装后启动管理界面
$ sudo system-config-samba        （也可以在点击菜单项进去：系统－系统管理－Samba）
```


Notes: 上面的安装步骤在相同的系统内经过验证的


