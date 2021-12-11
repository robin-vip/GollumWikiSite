# dokuWiki

操作系统： ubuntu 20.04

## 安装  
1. 安装 php

2. 下载dokuWiki安装包  
点击[Download DokuWiki!](https://download.dokuwiki.org/)下载


3. 解压后将其拷贝到/var/www/html目录下
```
# tar zxvf dokuwiki-stable.tgz
# mv dokuwiki-2020-07-29 /var/www/html/dokuwiki
```

4. 设置权限
```
cd dokuwiki
sudo chown -R www-data:www-data data conf
```

5. 安装 http://127.0.0.1/dokuwiki/install.php

## FAQ
1. 安装dokuWiKi时在浏览器中输入`http://192.168.56.100/dokuwiki/install.php`有如下错误提示
```
The installer found some problems, indicated below. You can not continue until you have 
fixed them.

    PHP function xml_parser_create is not available. Maybe your hosting provider 
    disabled it for some reason?
```
解决方法如下：
```  
# sudo apt-get install php-xml                // 安装php-xml
# sudo /etc/init.d/apache2 restart            // 重启web server
```

## link
_**[ubuntu下安装dokuwiki](https://blog.csdn.net/weixin_33989058/article/details/91922408)**_  
_**[DokuWiki Installer](https://www.dokuwiki.org/installer)**_  
_**[Security](https://www.dokuwiki.org/security#web_access_security)**_  
