# 22.3.2 添加主存储异常处理

1. 错误的NFS Server的IP地址、错误的NFS共享目录、错误的NFS挂载参数。

2. 错误的Ceph IP地址，错误的Ceph SSH 端口，错误用户名密码，用户名没有sudo权限，Ceph集群未配置好。

3. 错误的FusionStor IP地址，错误的FusionStor SSH 端口，错误用户名密码，用户名没有sudo权限，FusionStor集群未配置好。

4. NFS或者Ceph的防火墙或者Iptables禁用了访问连接。

5. NFS或者Shared Mount Point提供的目录未提供读写权限。

