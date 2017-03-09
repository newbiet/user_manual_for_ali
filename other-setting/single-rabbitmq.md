# 23.3 配置独立的RabbitMQ服务器

同样可以使用 zstack-ctl 来完成RabbitMQ服务的安装：

```
sudo zstack-ctl install_rabbitmq
 --host=RABBITMQ_MACHINE_IP
```

当成功的安装了RabbitMQ之后，还需要为远程的RabbitMQ访问创建加密访问(需要在RabbitMQ的服务器上做如下操作)：

```
rabbitmqctl add_user zstack ZSTACK_USER_PASSWORD
rabbitmqctl set_user_tags zstack administrator
rabbitmqctl change_password zstack ZSTACK_USER_PASSWORD
rabbitmqctl set_permissions -p / zstack ".*" ".*" ".*"
```

另外还需要把RabbitMQ的加密访问配置记录到zstack.properties(在ZStack管理节点做如下步骤)：

```
zstack-ctl configure CloudBus.rabbitmqUsername=zstack
zstack-ctl configure \
CloudBus.rabbitmqPassword= ZSTACK_USER_PASSWORD
zstack-ctl save_config
```

当用户安装有多个管理节点的时候，需要到每个管理节点上配置正确的RabbitMQ访问方式，配置方式详见23.4 zstack.properties文件。

