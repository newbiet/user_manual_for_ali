# 23.8 数据库备份与恢复  

为保护数据安全，防止数据丢失，系统现已主动定期进行数据库备份。默认使用crontab进行控制。

用户使用crontab -l命令可查看管理节点相关的自动定时备份任务。

用户也可以使用crontab-e的界面里修改备份策略，默认为每天的夜间十二点半和中午12点半进行备份，并且最多保留最新的14次备份。

默认的数据库备份文件存放路径：/var/lib/zstack/mysql-backup/

建议用户使用异地备份策略来提高安全性。只要数据库文件存在，即使系统的相关机器挂掉，均可使用数据库文件进行恢复。

`[root@localhost ~]#crontab –l|grep mysql

30 0,12 * * * zstack-ctl dump_mysql --keep-amount 14

表示每天夜间12点半和中午12点半进行数据库备份，并保存最新的14次备份`

以下命令会恢复指定的数据库文件，以防万一，在恢复数据库之前，系统会再次对当前的数据库进行备份。恢复过程中会停止相关的管理节点服务并在恢复数据库
后，重新开启服务。

> [root@localhost ~]# zstack-ctl dump_mysql --keep-amount 14

`Backup mysql successful! You can check the file at /var/lib/zstack/mysql-backup/zstack-backup-db-2016-06-28_23-52-33.gz`                                                                                                                       
> [root@localhost~]#zstack-ctl restore_mysql –f backup.gz --mysql-root-password root.password

`Backup mysql before restore data ...
Backup mysql successful! 
You can check the file at /var/lib/zstack/mysql-backup/zstack-backup-db-2016-06-28_23-23-40.gz
the management node has been stopped
Starting recover data ...
Recover data successfully!`

`backup.gz代表待恢复的数据库文件
root.password 代表当前数据库的root用户密码`


