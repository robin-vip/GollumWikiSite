# user manager

Ubuntu系统

## 添加用户
1. 添加用户
```
sudo adduser username
```
其中username是你要创建的用户的名字，然后设置密码还有相关信息就可以了

2. sudo权限
用adduser创建后的新用户是不能使用sudo的，因为还没有赋予相关root权限，执行以下代码赋予权限
```
sudo usermod -a -G adm username
sudo usermod -a -G sudo username
```

## 删除用户
1. 只删除用户
```
sudo userdel username
```
2. 删除用户和/home目录对应的username目录（包括对应路径下的所有文件）
```
sudo userdel -r username
```

