<h1>Install Gogs from source code</h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)

1. [安装golang](/it/complier/Install-Golang)

2. [安装mysql](/it/mysql/Install-Mysql)

3. 下载gogs源码
  ```
  $ go get -u github.com/gogs/gogs
  ```

4. 编译
  ```
  $ cd $GOPATH/src/github.com/gogs/gogs
  $ go build
  测试安装
  $ ./gogs web
  (运行上面的没有错误，说明编译成功，直接Ctrl+C退出即可。)
  ```

5. 安装
  ```
  $ cd $GOPATH/src/github.com/gogits/gogs/scripts
  $ ./build.sh
  (按实际系统执行scripts文件夹中的相关脚本)
  $ sudo cp -fa output /usr/local/gogs
  $ sudo chown -R git:git /usr/local/gogs
  ```

6. 配置  
  a. 配置数据库
  ```
  $ mysql -u root -p
  mysql> create user 'gogs'@'localhost' identified by '123456';
  mysql> grant all privileges on gogs.* to 'gogs'@'localhost';
  mysql> flush privileges;
  mysql> create database gogs character set utf8;
  ```
  b. 配置gogs
  ```
  $ cd /usr/local/gogs
  $ mkdir -p custom/conf
  $ cp conf/app.ini custom/conf/app.ini
  ```
  修改配置 (参考 [gogs configuration](https://gogs.io/docs/advanced/configuration_cheat_sheet))
  ```
  $ vi custom/conf/app.ini
  ```
  [local gogs configuration](/it/server/git/gogs_configuration)
  
gogs缺省的端口号是3000