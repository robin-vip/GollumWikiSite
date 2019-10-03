<h1>Install Mysql</h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)

1. 安装Java8  
  a. 下载 [jre-8u221-linux-i586.tar.gz](https://pan.baidu.com/s/1zU124nYybpuhyWaCGj1FbA)  
  (下载地址：https://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html)

  b. 安装  
  ```
  $ sudo tar zxvf jre-8u221-linux-i586.tar.gz  -C /usr/local
  ```

  c. 配置
  ```
  $ vi ~/.profile
  ```
  (将下面的内容添加到文件末尾)
  ```
  # set PATH so it includes user's java8 bin if it exists
  if [ -d "/usr/local/jre1.8.0_221" ] ; then
      export JAVA_HOME=/usr/local/jre1.8.0_221
      PATH="$JAVA_HOME/bin:$PATH"
  fi
  ```
