# 23.12 升级ZStack定制版ISO的yum源

如果之前使用了ZStack定制版 CentOS 7.2 低版本的ISO（例如1.2版本）安装好了系统，在升级系统之前，需要先升级相关的yum源。

升级步骤如下:

`cd /opt/`

`wget http://download.zstack.org/ISO/ZStack-Community-x86_64-DVD-160827.iso`

`wget http://www.系统.com/downloads/scripts/zstack-repo-upgrade.sh`

`bash /opt/zstack-repo-upgrade.sh`

`http://download.zstack.org/ISO/ZStack-Community-x86_64-DVD-160827.iso`可换成最新版本的ZStack定制版ISO


