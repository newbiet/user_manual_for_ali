# 23.10 本地存储空间扩容

在使用系统产品的过程中， 如果存储空间容量不足，可以通过以下方式进行存储空间扩容。以下为系统主存储空间/zstack_ps扩容的样例：

1.设置待扩容之物理机进入维护模式

2.插入新的大容量磁盘至物理机，并进行分区格式化，假如设备名称为/dev/sdc

3.创建新目录/new_volume，挂载此磁盘mount /dev/sdc1 /new_volume

4.执行rsync -a /zstack_ps /new_volume/拷贝原始的磁盘文件至新磁盘

5.添加以下内容至/etc/fstab，将物理磁盘挂载点与/zstack_ps目录绑定

/dev/sdc1         /new_volume            auto    defaults        0   0

/new_volume      /zstack_ps               none    defaults,bind   0  0

6.重启物理机，使用“df -h /zstack_ps”检查扩容后的空间增量

Filesystem    Size  Used  Avail  Used%  Mounted on

/dev/vdb1     4.0T  304G   3.5T      8%   /zstack_ps


7.重启系统服务

`zstack-ctl stop`

`zstack-ctl start`

8.重连Host继续使用系统

注意: 备份存储的扩容方法与此类似，只是无须对Host进行维护模式及重连的操作。
 
