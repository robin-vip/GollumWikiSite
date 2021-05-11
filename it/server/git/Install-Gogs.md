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
  

# 使用说明
1. gogs缺省的端口号是3000

2. **备份与恢复**  
论坛链接： [How to backup, restore and migrate](https://discuss.gogs.io/t/how-to-backup-restore-and-migrate/991)  
The follow is copied from offcial forum  
**Important Notes**
* This post is based on Gogs 0.10.18.0313.  
* If you’re trying to restore to PostgrsSQL, you need at least 0.11.11.0521.  

    Other than pack up `gogs-repositories`, `custom` and database separately, Gogs provides two commands for unified process of **backup**, **restore** and even **migrate to another database engine**.  

    **Backup**  
Go to the directory where your Gogs binary is located, and execute following command:  
```
./gogs backup
```
Without any flags, `backup` command will pack up all `gogs-repositories`, `custom` and database into a single zip archive (e.g. `gogs-backup-xxx.zip`) under current directory.  
It could be a bad idea if your `gogs-repositories` contains GB of raw data, in that case, you can apply `--exclude-repos` flag:
```
./gogs backup --exclude-repos
```
If your `custom/conf/app.ini` is somewhere unusual, make sure you specify it via `--config` flag like always:  
```
./gogs backup --config=my/custom/conf/app.ini
```

    **Database**  
If you’re only interested in backup database, or want to migrate from one database engine (e.g. SQLite3) to another engine (e.g. MySQL), `--database-only` is your friend:  
```
./gogs backup --database-only
```
The backup format of database are portable JSON files, each file corresponds to a database table, you can do whatever you want with those files.  

    **Restore**  
The `restore` command also has flags to indicate only restore database or everything in backup archive:  
```
./gogs restore --database-only --from="gogs-backup-xxx.zip"
```
If a table that is not presented in backup archive, whatever in current database table will remain unchanged.  

    **Custom config file**  
There are 3 steps to determine which `custom/conf/app.ini` command uses:  
    1. Use the one you specified vis flag `--config`.  
    2. Use the one stored in backup archive.  
    3. Use the one in `$(pwd)/custom/conf/app.ini`.  
If all 3 steps failed, sorry, impossible to perform restore process.


