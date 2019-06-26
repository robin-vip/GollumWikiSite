<h1>Install Mysql</h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)

1. sudo apt-get install mysql-server  
(安装过程中会要求输入database root用户的密码)

2. sudo apt-get install mysql-client

3. sudo apt-get install libmysqlclient-dev

4. 检查是否安装成功  
    sudo netstat -tap | grep mysql  
    通过上述命令检查之后，如果看到有mysql 的socket处于 listen 状态则表示安装成功。
    <pre>tcp        0      0 localhost:mysql         *:*                     LISTEN      25476/mysqld</pre>

5. 登录数据库  
mysql -u root -p

6. mysql简单使用：  
    6.1. 创建用户  
        ```mysql> CREATE USER mm_wiki_u IDENTIFIED BY 'p@word';    //IDENTIFIED BY 'p@word'给出口令```  
    6.2. 创建数据库  
        ```mysql> CREATE DATABASE mm_wiki;```  
    6.3. 授权mm_wiki_u用户拥有mm_wiki数据库的所有权限  
        ```mysql> GRANT ALL PRIVILEGES ON mm_wiki.* TO mm_wiki_u@localhost IDENTIFIED BY 'p@word';```  
        ```mysql> FLUSH PRIVILEGES;```  
    6.4. 更改mm_wiki_u用户密码  
        ```SET PASSWORD FOR mm_wiki_u = Password('新密码');```