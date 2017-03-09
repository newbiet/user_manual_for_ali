# 23.2 配置独立的MySQL服务器

系统在安装过程中会配置一个本地的数据库。您也可以安装独立的MySQL数据库。安装独立的MySQL数据库后，您需使用下面的系统工具来初始化数据库，并进行对应的设置。其中MYSQL_ROOT_PASSWORD是MySQL的根用户密码，MYSQL_ZSTACK_PASSWORD是用户希望设置的zstack用户的MySQL密码，MYSQL_SERVER_IP是mysql数据库的物理机IP地址。输入命令后，会要求用户输入MYSQL服务器的ssh密码用于远程登录：

```
sudo zstack-ctl deploydb \
--root-password="MYSQL_ROOT_PASSWORD" \
--zstack-password="MYSQL_ZSTACK_PASSWORD" \
--host=”MYSQL_SERVER_IP”
```


