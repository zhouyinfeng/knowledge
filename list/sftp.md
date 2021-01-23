# sftp
## 新增sftp测试账号 useradd -d /home/zyfsftp -m zyfsftp -g sftponly
-d 指定某个目录成为家目录，使用绝对路径
-g 后面接的组名就是上面提到的initial group
-s 后面接一个shell 如没有指定 则预设是/bin/bash
## 修改sftp账号的密码
 passwd
 zyfsftp
 ## 修改sftp账号的家目录属主
 chown root:root /home/zyfsftp
 ## 修改sftp账号的家目录权限为755
 chmod 755
 /home/zyfsftp
 ## 测试sftp账号是否可用
 sftp -o
 port=20022
 zyfsftp@177.2.21.53
 这个命令是在VMportal后台上执行的
 输入用户名密码后，出现如下信息表示简历成功
 connected to 177.2.21.53
 sftp>
