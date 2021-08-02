## 准备一台redhat服务器
##  配置jdk变量
### 到java官网下载jdk 选择jre-11.0.8-linux-x64.tar.gz，上传到/usr/local目录下，并解压
### 编辑/etc/profile 文件，最后加上如下几行，配置profile文件
    export JAVA_HOME=/usr/lib/jvm/java-1.7.0-openjdk-1.7.0.45.x86_64/jre  (指的是jdk的路径)
    export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
    export PATH=$PATH:$JAVA_HOME/bin

### source /etc/profile
java -version 检查jdk是否正常

## 安装tomcat
### 在官网上下载安装包 http://tomcat.apache.org
    上传安装包，移动安装包到opt目录下，解压，将解压后的文件名改为tomcat
    mv apache-tomact-8.5.45.tar.gz /opt
    cd /opt
    tar -xzvf  apache-tomact-8.5.45.tar.gz
    mv  apache-tomact-8.5.45.tar.gz tomcat

    启动tomcat
    /opt/tomcat/bin/startup.sh

### 验证 ip:8080
如果出现404 修改配置文件 
vim /opt/comcat/conf/web.xml
设置listening取值为true
<init-param>
    <param-name>listening</param-name>
    <param-name>true</param-name>
</init-param>

重启tomcat
/opt/tomcat/bin/shutdown.sh
/opt/tomcat/bin/startup.sh

### 增加虚拟映射目录
server.xml中HOST节点中，增加如下配置，其中/home/content是自己定义的目录
<Context path="/web" docBase="/home/content"/>
验证  ip:8080/web/目录名

### apache 支持put操作
在web.xml文件中添加如下配置
<init-param>
    <param-name>readonly</param-name>
    <param-name>tfalse</param-name>
</init-param>

重启tomcat
/opt/tomcat/bin/shutdown.sh
/opt/tomcat/bin/startup.sh

