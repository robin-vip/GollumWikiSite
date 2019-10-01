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
  #### cmake 配置  
  cmake option | configure option | Parameter option  
  | ---- | ---- | ---- |   
  | -DCMAKE_INSTALL_PREFIX=/usr/local/mysql | --prefix=/usr/local/mysql | 设置mysql安装目录 |  
  | -DMYSQL_DATADIR=/usr/local/mysql/data | --localstatedir=/usr/local/mysql/data |   设置mysql数据库文件目录 |  
  | -DSYSCONFDIR=/usr/local/mysql/conf | --sysconfdir=/usr/local/mysql/conf |   设置MySQL参数文件的默认路径，这一选项可以在MySQL服务启动时通过defaults-file参数进行设置 |  
  | -DWITH_MYISAM_STORAGE_ENGINE=1 |  | 安装 MyISAM存储引擎 |  
  | -DWITH_INNOBASE_STORAGE_ENGINE=1 || 安装 InnoDB存储引擎 |  
  | -DWITH_MEMORY_STORAGE_ENGINE=1 || 安装 Memory存储引擎 |  
  | -DWITH_READLINE=1 || 设置输入输出的处理方式(5.1及之前版本，5.6.5及以上版本不需要处理)|  
  | -DMYSQL_UNIX_ADDR=/tmp/mysql.sock || 设置监听套接字路径，这必须是一个绝对路径名。 |  
  | -DMYSQL_TCP_PORT=3306 || 设置监听端口 |  
  | -DENABLED_LOCAL_INFILE=1 || 是否允许从客户端本地加载数据到MySQL服务端，专用于load data infile语句，默认是不允许的 |  
  | -DWITH_PARTITION_STORAGE_ENGINE=1 || 安装分区存储引擎 |  
  | -DEXTRA_CHARSETS=all || 安装所有扩展字符集 |  
  | -DDEFAULT_CHARSET=utf8 || 设置MySQL服务的默认字符集（缺省是latin1） |  
  | -DDEFAULT_COLLATION=utf8_general_ci || 设置MySQL服务的默认校对规则，本参数的默认值为latinl_swedish_ci，这一选项在MySQL服务启动时也可以通过collation_server参数进行设置 | 
  注：重新运行配置，需要删除CMakeCache.txt文件

3. 配置和启动Mysql服务  
  a. 修改mysql目录所有者和组
  ```
  $ sudo chown -R sunrise:sunrise /usr/local/mysql
  ```
  b. 确定配置文件路径  
  ```
  $ cd /usr/local/mysql
  $ mkdir conf
  $ cp support-files/my-large.cnf conf/my.cnf
  ```
  support-files目录中有my-small.ini、my-medium.ini、my-large.ini、my-huge.ini等配置文件，分别用于不同的硬件环境。
  ```
  my-small.cnf                （内存 <= 64M）
  my-medium.cnf               （内存 128M）
  my-large.cnf                （内存 512M）
  my-huge.cnf                 （内存 1G-2G）
  my-innodb-heavy-4G.cnf      （内存 4GB）
  ```
  c. 修改my.cnf配置文件
  ```
  $ vi conf/my.cnf
  在[mysqld]下添加"skip-name-resolve".（禁止DNS解析）  
  mysql主机查询DNS很慢或是有很多客户端主机时会导致连接很慢，如果开发机器是不能够连接外网的（没有域名），所以DNS解析是不可能完成的，从而也就明白了为什么连接那么慢了。同时，请注意在增加该配置参数后，mysql的授权表中的host字段就不能够使用域名而只能够使用 ip地址了，因为这是禁止了域名解析的结果。 
  ``` 
  d. 修改PATH变量
  ```
  $ vi ~/.profile
  ```
  将下面的内容添加的文件末尾
  ```
  # set PATH so it includes user's mysql bin if it exists
  if [ -d "/usr/local/mysql/bin" ] ; then
      PATH="/usr/local/mysql/bin:$PATH"
  fi
  ```
  执行下面的命令，让其立即生效
  ```
  $ source ~/.profile
  ```
  e. 初始化mysql数据库
  ```
  $ ./scripts/mysql_install_db --user=sunrise --basedir=/usr/local/mysql --datadir=/usr/local/mysql/data
  ```
  f. 设置mysql服务
  ```
  $ sudo cp support-files/mysql.server /etc/init.d/mysqld
  ```
  g. 启动mysql服务
  ```
  $ service mysqld start
  ```
  查看服务是否启动
  ```
  $ netstat -tulnp | grep 3306 
  $ mysql -u root -p   
  (密码为空，如果能登陆上，则安装成功。)
  ```
  h. 配置mysql用户root的密码
  ```
  $ mysqladmin -u root password '123456'
  ```
  







