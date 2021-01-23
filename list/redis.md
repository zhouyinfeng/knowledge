# linux安装redis
## 解压 
tar -xzvf redis
## 安装
cd redis
cd src
make install PREFIX=/usr/local/redis
## 移动配置文件到安装目录
cd ../
mkdir /usr/local/redis/etc
mv redis.conf /usr/local/redis/etc
## 配置redis为后台启动
. vi /usr/local/redis/etc/redis.conf //将daemonize no改成daemonize yes
. bind 127.0.0.1改为 #bind 127.0.0.1  (注释掉)
. protected-mode yes 改为 protected-mode no
## 将redis加入到开机启动
vi /etc/rc.local  //在里面添加内容：
/usr/local/redis/bin/redis-server /usr/local/redis/etc/redis.conf  (意思是开机调用这个开启redis的命令)
## 开启redis
/usr/local/redis/bin/redis-server /usr/local/redis/etc/redis.conf

# 常用命令
redis-server /usr/local/redis/etc/redis.conf    //启动redis
pkill redis  //停止redis
卸载redis  rm -rf /usr/local/redis  删除所有redis相关命令  rm -rf /usr/bin/redis-*
珊瑚redis解压文件夹 rm-rf /root/download/redis
