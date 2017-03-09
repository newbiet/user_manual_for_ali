# 3.3 ZStack专家模式

如果用户选择专家模式，重启后会进入term界面。

ZStack-Enterprise-Installation的root密码为：password

安装步骤如下：

1. 进入`/opt`目录，执行`bash zstack-enterprise-installer.bin` 进行离线安装（默认带-o参数）

2. 在安装系统前，如果用户已经配置了MySQL数据库，并设置了数据库的root用户密码，请在安装时使用参数：“-P MYSQL_ROOT_PASSWORD”。如果用户没有预先设置MySQL root 用户密码，为了安全考虑，ZStack安装程序将会主动设置一个root用户密码，具体的密码可以从安装完成后的屏幕输出获得。用户可以根据屏幕输出的提示来修改数据库root用户密码。如果用户有多网络，用户可以指定特定网络来安装，例如`bash zstack-enterprise-installer.bin  -I eth0 `或者`bash mevoco-installer.bin -I 192.168.0.1`分别代表使用eth0的网卡或192.168.0.1的网络进行安装。

3. 安装成功后，安装程序会提示相关可访问的URL，以进行系统Web界面管理，例如: `http://172.20.11.11:5000` 。

安装完毕的界面如图3-3-1所示。请仔细阅读安装完成后的屏幕的输出以获取更多信息。

![png](../images/3-3-1.png "图3-3-1 安装完成界面")
###### 图3-3-1 安装完成界面


**注意：**如下图所示，ZStack安装完成后会自动安装nfs服务和http服务，分别为主存储和镜像服务器的测试目录。请勿将生产环境的主存储和镜像备份目录放在这两个目录。安装过程中遇到的异常，请参考[安装异常处理](/exception/install.md)。 

