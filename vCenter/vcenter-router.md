# vCenter云路由

从[云路由](/Network/VR-README.md)章节可以了解到，云路由是一台特殊的云主机，可以提供多种网络服务。包括：DHCP、DNS、SNAT、EIP、端口转发、IPsec隧道、端口转发等。

在ZStack中接管的vCenter支持创建一个针对vCenter的云路由，只需要添加一个对应的云路由镜像，操作与ZStack云路由完全相同。

在vCenter云路由网络中，添加网络（云路由）可以分为添加公有网络、添加云路由镜像、添加云路由规格、添加私有网络四个部分。参考[网络设置（云路由）](/Network/VR-network.md)。

