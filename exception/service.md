# 22.1.3 服务异常处理

1. 若启动服务超时，则可以在启动服务的命令行中加入--timeout 400增加启动超时时限，例如 `zstack_ctl start_node –timeout 400`

2. 执行`zstack-ctl status`检查服务的状态，根据相应提示查看management-server.log，定位问题所在。

3. 若需重启系统服务，请执行`zstack-ctl stop; zstack-ctl start`

