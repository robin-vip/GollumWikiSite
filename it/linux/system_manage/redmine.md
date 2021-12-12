# redmine
操作系统： ubuntu 20.04

## 安装
1. 下载redmine安装包并解压

2. 创建一个空数据库(mysql)
```
# sudo mysql -u root -p
CREATE DATABASE redmine CHARACTER SET utf8mb4;
CREATE USER 'redmine'@'localhost' IDENTIFIED BY 'my_password';
GRANT ALL PRIVILEGES ON redmine.* TO 'redmine'@'localhost';
```

3. 数据库连接配置
```
将config/database.yml.example 复制命名为config/database.yml并配置数据库设置
(主要是设置数据库账号名和密码)
```

4. 安装ruby
```
# sudo apt-get install ruby-full
```
判断是否安装完成
```
# ruby --version
# gem --version
```

5. 安装rails
```
# sudo gem install rails    // 很有可能安装失败, 也可以本地安装sudo gem  install --local  rails-5.2.0.gem 
手动安装需要预先下载依赖的gem包 (https://rubygems.org/downloads/rails-5.2.0.gem)
```

6. 安装依赖
```
# sudo gem install bundler

# bundle install --without development test              // 安装 redmine需要的gems
安装过程中可能会碰到如下mysql2错误：
Installing mysql2 0.5.3 with native extensions
Gem::Ext::BuildError: ERROR: Failed to build gem native extension.
...
/usr/lib/ruby/2.7.0/mkmf.rb:1050:in `block in find_library': undefined method `split' for nil:NilClass (NoMethodError)
        from /usr/lib/ruby/2.7.0/mkmf.rb:1050:in `collect'
        from /usr/lib/ruby/2.7.0/mkmf.rb:1050:in `find_library'
        from extconf.rb:87:in `<main>'
可以通过下面的安装相关包解决
# sudo apt-get install default-libmysqlclient-dev
```

7. 会话数据保护密钥
```
# bundle exec rake generate_secret_token
```

8. 设置数据库表结构  
在redmine根目录下执行以下命令
```
# RAILS_ENV=production bundle exec rake db:migrate
```
如果在ubuntu系统出现如下错误：
```
Rake aborted!
no such file to load -- net/https
```
可以通过安装libopenssl-ruby1.8 解决
```
# sudo apt-get install libopenssl-ruby1.8
```

9. 数据库缺省数据集
通过以下命令插入缺省的配置数据到数据库中
```
# RAILS_ENV=production bundle exec rake redmine:load_default_data
期间需要选择语言，如果事先定义REDMINE_LANG变量，这这条命令运行期间则不再需要输入了。例如：
# RAILS_ENV=production REDMINE_LANG=zh bundle exec rake redmine:load_default_data
```

10. 文件系统权限
redmine运行账号必须有以下子目录的写入权限
* files (storage of attachments 保存附件)
* log (application log file production.log 日志文件)
* tmp and tmp/pdf (create these ones if not present, used to generate PDF documents among other things)
* public/plugin_assets (assets of plugins)  
假定运行redmine的账号是redmine，可以通过以下命令设置权限
```
# mkdir -p tmp tmp/pdf public/plugin_assets
# sudo chown -R redmine:redmine files log tmp public/plugin_assets
# sudo chmod -R 755 files log tmp public/plugin_assets
```
如果在这些目录下已经存在文件（以前备份的），则需要确保这些文件没有可执行权限。可以通过以下命令处理：
```
# sudo find files log tmp public/plugin_assets -type f -exec chmod -x {} +
```

11. 安装测试
通过运行WEBrick web server来测试安装
```
# bundle exec rails server webrick -e production
```
webrick 启动后，可以浏览网址: http://localhost:3000/, 然后可以看到欢迎页面  
注意： webrick 只能用于安装和测试，真正使用只能用Passenger (aka mod_rails), FCGI or a Rack server (Unicorn, Thin, Puma, hellip;) 启动redmine服务。

12. 登录
缺省账号：
```
login: admin
password: admin
```
登录后按页面提示修改密码。  
可以在管理员菜单中选择setting修改大部分app设置

## 配置
1. 配置文件是保存在config/configuration.yml文件中；

2. 通过以下命令恢复默认配置
```
# cp config/configuration.yml.example config/configuration.yml   // 配置改变后需要重启服务服务
```

3. 设置开机启动
创建并打开文件
```
sudo vi /etc/init.d/redmine
```
输入如下内容：
```
#!/bin/sh
# 
# description: Auto-starts redmine
# processname: redmine
cd /home/$user_name/workspace/redmine-4.2.3 && ruby script/rails server webrick -e production
```
添加可执行权限
```
chmod 755 /etc/init.d/redmine
```

## link

_**[redmine download](https://www.redmine.org/projects/redmine/wiki/Download)**_  
_**[redmine installation guide](https://www.redmine.org/projects/redmine/wiki/RedmineInstall#Optional-components)**_



