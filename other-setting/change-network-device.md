# 23.9 CentOS7网卡设备编号变更

本节主要描述配置物理网卡网络命令：`zs-network-setting`

`zs-network-setting`的使用信息如下：

1.参数“-i”，意为对接口（interface）配置网络地址

zs-network-setting -i [interface] [ipaddress] [netmask] [gateway]
                    
> 例子：zs-network-setting -i eth0 192.168.1.10 255.255.255.0 192.168.1.1

2.参数“-b”，意为基于接口（interface）创建网桥（bridge）并配置网络地址


zs-network-setting -b [interface] [ipaddress] [netmask] [gateway]
                     
> 例子：zs-network-setting -b eth0 192.168.1.10 255.255.255.0 192.168.1.1



* 注意：此命令作用在物理接口上，网关是可选参数。


* 注意：系统识别网桥名为“br_”前缀，管理员无需更名。
