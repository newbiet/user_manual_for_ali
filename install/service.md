# 3.4 部署系统服务

1.在首次安装后，系统将自动启动ZStack服务。

2.管理节点重启后，ZStack服务将自动开机自启。

3.在管理节点因维护或其他异常原因停止服务后，需手动启动服务。启动ZStack服务的方法为：
```
[root@localhost ~]#zstack-ctl start
#此命令将同时启动管理节点和WEB UI服务
```

4.用户可以使用以下命令查看系统管理节点相关服务的运行状态。

```
[root@172-20-12-20 ~]# zstack-ctl status
ZSTACK_HOME: /usr/local/zstack/apache-tomcat/webapps/zstack
zstack.properties: /usr/local/zstack/apache-tomcat/webapps/zstack/WEB-INF/classes/zstack.properties
log4j2.xml: /usr/local/zstack/apache-tomcat/webapps/zstack/WEB-INF/classes/log4j2.xml
PID file: /usr/local/zstack/management-server.pid
log file: /usr/local/zstack/apache-tomcat/logs/management-server.log
MN status: Running [PID:30203]
UI status: Running [PID:31287] http://172.20.12.20:5000
```

5.用户也可以使用以下命令单独查看Web UI服务状态。

```
[root@172-20-12-20 ~]# zstack-ctl ui_status
UI status: Running [PID:31287] http://172.20.12.20:5000

```

6.在使用过程中如需重启管理节点服务，则需执行

```zstack-ctl restart_node```

7.在使用过程中不建议全部停止及重启所有服务。如果确需重启所有服务，可执行以下命令进行重启。

```zstack-ctl stop && zstack-ctl start``` 

注意：启动服务过程中遇到的异常，请参考[服务异常处理](/exception/service.md)。
