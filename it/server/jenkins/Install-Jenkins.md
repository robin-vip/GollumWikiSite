<h1>Install Jenkins</h1>
操作系统：Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-32-generic i686)

1. 安装Java8  
  a. 下载 [jre-8u221-linux-i586.tar.gz](https://pan.baidu.com/s/1zU124nYybpuhyWaCGj1FbA)  
  (下载地址：https://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html)  
  b. 安装  
  ```
  $ sudo tar zxvf jre-8u221-linux-i586.tar.gz  -C /usr/local
  $ sudo chown sunrise:sunrise -R /usr/local/apache-tomcat-7.0.96
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
  使配置生效
  ```
  $ source ~/.profile
  ```
  
2. 安装tomcat
  a. 下载 [apache-tomcat-7.0.96.tar.gz](https://pan.baidu.com/s/1XaVYBsGfQjiV1y3rSGf1aQ)  
  (下载地址： https://tomcat.apache.org/download-70.cgi 选择Binary Distributions -> Core -> tar.gz)
  b. 安装
  ```
  $ sudo tar zxvf apache-tomcat-7.0.96.tar.gz -C /usr/local/
  ```
  
3. 安装jenkins  
  a. 下载 [jenkins_2.190.1_all.deb](https://pan.baidu.com/s/16asybDOLlgMCu74mSBue_g)  
  (下载地址：https://jenkins.io/zh/download/)  
  b. 安装  
  ```
  $ dpkg -X jenkins_2.190.1_all.deb jenkins
  $ cp jenkins/usr/share/jenkins/jenkins.war /usr/local/apache-tomcat-7.0.96/webapps/
  ```
  c. 初始化运行配置  
  ```
  $ /usr/local/apache-tomcat-7.0.96/bin/startup.sh
  在浏览器输入：http://192.168.128.3:8080/jenkins/
  根据提示进行初始化设置
  ```
  ```
  vi ~/StartupTask/task_table.sh
  ```
  将下面的内容添加到文件末尾
  ```
  if [ -f "/usr/local/apache-tomcat-7.0.96/bin/startup.sh" ];then
      echo "Start jenkins serverice.(base on tomcat)"
      /usr/local/apache-tomcat-7.0.96/bin/startup.sh
  fi
  ```
  jenkins的配置数据保存在"~/.jenkins"目录
  
参考:  
https://www.yiibai.com/jenkins





