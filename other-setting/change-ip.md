# 23.5 更新系统相关服务器IP地址

当系统环境（例如管理节点IP地址，数据IP地址，数据库用户访问密码等）变更，需要更新系统相关服务器IP地址。更新IP地址后需重启系统服务。

如果所有服务均安装在同一管理节点，则只需执行以下命令即可更新。

> [root@localhost ~]# zstack-ctl change_ip --ip 172.23.11.89

`Update cloudbus server ip 172.23.11.89 in /usr/local/zstack/apache-tomcat/webapps/zstack/WEB-INF/classes/zstack.properties`

`Update management server ip 172.23.11.89 in /usr/local/zstack/apache-tomcat/webapps/zstack/WEB-INF/classes/zstack.properties`

`Update mysql new url jdbc:mysql://172.23.11.89:3306 in /usr/local/zstack/apache-tomcat/webapps/zstack/WEB-INF/classes/zstack.properties`

`Update new ip address 172.23.11.89 in /usr/local/zstack/kairosdb/conf/kairosdb.properties`

`Update kairosdb ip 172.23.11.89 in /usr/local/zstack/apache-tomcat/webapps/zstack/WEB-INF/classes/zstack.properties`

`Update cassandra listen address: 172.23.11.89 rpc_address: 172.23.11.89 in /usr/local/zstack/apache-cassandra-2.2.3/conf/cassandra.yaml`

`Update cassandra rpc address: 172.23.11.89 in /usr/local/zstack/apache-tomcat/webapps/zstack/WEB-INF/classes/zstack.properties`

如果用户对Cloudbus, MySQL, Kairosdb和Cassandra服务分别部署了独立的服务器，也可通过“zstack-ctl change_ip”命令附加相应的参数进行更新相关服务，例如，下例对管理节点、MySQL和Cassandra同时更新IP地址。如需对其他服务器进行更新可参考“zstack-ctl change_ip -h”帮助文件进行相应更新。

> [root@localhost ~]# zstack-ctl change_ip --ip 172.23.12.44 --mysql_ip 172.23.12.45 --cassandra_rpc_address 172.23.12.45 --cassandra_listen_address 172.23.12.45

`Update cloudbus server ip 172.23.12.44 in /usr/local/zstack/apache-tomcat/webapps/zstack/WEB-INF/classes/zstack.properties`

`Update mysql new url jdbc:mysql://172.23.12.45:3306 in /usr/local/zstack/apache-tomcat/webapps/zstack/WEB-INF/classes/zstack.properties`

`Update new ip address 172.23.12.44 in /usr/local/zstack/kairosdb/conf/kairosdb.properties`

`Update kairosdb ip 172.23.12.44 in /usr/local/zstack/apache-tomcat/webapps/zstack/WEB-INF/classes/zstack.properties`

`Update cassandra listen address: 172.23.12.45 rpc_address: 172.23.12.45 in /usr/local/zstack/apache-cassandra-2.2.3/conf/cassandra.yaml`

`Update cassandra rpc address: 172.23.12.45 in /usr/local/zstack/apache-tomcat/webapps/zstack/WEB-INF/classes/zstack.properties`
