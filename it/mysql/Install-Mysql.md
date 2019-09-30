<h1>Install Mysql</h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)
## dpkg安装
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

## 源码安装
1. 安装cmake  ([cmake-v3.0.2.tar.gz](https://pan.baidu.com/s/1rGlDObdLOyVCTR5dsUi3pg]))  
  ```
  $ tar zxvf cmake-v3.0.2.tar.gz 
  $ cd cmake-v3.0.2
  $ ./bootstrap && make 
  $ sudo make install
  ```
  [cmake代码仓库链接](git@gitlab.kitware.com:cmake/cmake.git)  
  
2. 编译安装mysql ([mysql-5.5.62.tar.gz](https://pan.baidu.com/s/1dw31xIqEym0_3SfaiZinUg))  
  ```
  $ tar zxvf  mysql-5.5.62.tar.gz
  $ cd mysql-5.5.62 
  $ cmake -DCMAKE_INSTALL_PREFIX=/usr/local/mysql \
    -DMYSQL_DATADIR=/usr/local/mysql/data \
    -DSYSCONFDIR=/etc \
    -DWITH_MYISAM_STORAGE_ENGINE=1 \
    -DWITH_INNOBASE_STORAGE_ENGINE=1 \
    -DWITH_MEMORY_STORAGE_ENGINE=1 \
    -DWITH_READLINE=1 \
    -DMYSQL_UNIX_ADDR=/tmp/mysql.sock \
    -DMYSQL_TCP_PORT=3306 \
    -DENABLED_LOCAL_INFILE=1 \
    -DWITH_PARTITION_STORAGE_ENGINE=1 \
    -DEXTRA_CHARSETS=all \
    -DDEFAULT_CHARSET=utf8 \
    -DDEFAULT_COLLATION=utf8_general_ci 
  $ make
  $ sudo make install
  ```
  [mysql其它版本下载链接](https://downloads.mysql.com/archives/community/)  
  cmake 配置  
  
  cmake option | configure option | Parameter  |  
  -|-|-|    
  a|b|c|  
  
  -DCMAKE_INSTALL_PREFIX=/usr|--prefix=/usr|设置mysql安装目录|  

3. 







