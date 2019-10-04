# How to migrate SVN repository to GIT server
**准备： a.SVN上被迁移的仓库； b.windows git工具（别的git 工具也行，目的是用于将svn仓库转换成git仓库）； c.git server(git lab).**

1. **安装git** ([Git-2.23.0-64-bit](https://github.com/git-for-windows/git/releases/download/v2.23.0.windows.1/Git-2.23.0-64-bit.exe))
[安装以及配置方法](https://blog.csdn.net/u013295518/article/details/78746007)

2. **仓库转换**  
    2.1 准备转换  
a. 创建保存git仓库的目录：GitProject(可以使用实际的仓库名)  
b. 创建提交用户名的对应表： users.txt 格式如下：
```
svn_user1=git_user1<u1@compay.com>
svn_user2=git_user2<u2@compay.com>
svn_user3=git_user3<u3@compay.com>
svn_user4=git_user4<u4@compay.com>
Notes: svn_userx 是该仓库在SVN上提交者的用户名；git_userx是对应git仓库的用户名；"<>"中是用户的邮箱地址。
这些只是用来替换commit log中对应的信息。
```

   2.2 开始转换  
a. 安装git之后，在保存user.txt 和 GitProject目录 的同级目录下右击菜单选择“Git Bash Here”.  
b. 在bash界面输入如下命令：
```
git svn clone https://192.168.1.9/svn/projects/ProdSuite/SW/Source/Code/ProdSuite_new --no-metadata --authors-file=users.txt ProdSuite
```
参数说明
```  
git svn clone 是Git的迁移命令;  
https://192.168.1.9/svn/projects/ProdSuite/SW/Source/Code/ProdSuite_new 是svn服务器上仓库地址;  
--no-metadata 参数去除了svn上很多杂乱的参数信息，保留了清晰简洁的提交记录信息;  
-file=users.txt 为你的用户映射文件夹;  
GitProject 是刚刚新建的空白项目名文件夹;  
```

3. **push git 仓库到git server**  
a. 在git server上创建一个bare repository(空仓库)；  
b. git remote add origin  git_server_url  && git push origin master:development


