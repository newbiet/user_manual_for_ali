# 23.11 日志Log收集

在使用系统的过程中，如果需要技术支持，在遇到错误或者异常时，可以使用日志收集工具采集相应的log信息，并把log信息发送到相关的技术支持团队，进行相关的技术支持。

`zstack-ctl collect_log`会将相应的log信息打包到屏幕提示的压缩包中，可将此文件发给技术团队寻求相应的解决方案。

`[root@172-23-11-248 ~]# zstack-ctl collect_log`

`Collecting log from this management node ...`

`Collecting log from host: 172.23.11.248 ...`

`Collecting log from host: 172.23.12.238 ...`

`The collect log generate at: /root/collect-log-2016-05-26_14-53.tar.gz`
