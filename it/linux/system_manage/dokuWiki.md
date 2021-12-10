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

## link
_**[ubuntu下安装dokuwiki](https://blog.csdn.net/weixin_33989058/article/details/91922408)**_
