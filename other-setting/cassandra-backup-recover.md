# 23.13 系统 Cassandra数据库备份与恢复

系统已支持自动备份Cassandra，可以通过crontab-l 查看相关的定时任务

`[root@localhost ~]# zstack-ctl dump_cassandra`

`Backup cassandra zstack_billing successful!`

`You can check the file at`

`/var/lib/zstack/cassandra-backup/zstack-backup-cassandra-db-zstack_billing-2016-06-28_23-43-06.tgz`


在使用过程中，发生Cassandra数据丢失的情况下，可以恢复已经备份的数据库。

`[root@localhost ~]#crontab –l|grep cassandra`

`30 0,12 * * * zstack-ctl dump_cassandra --keep-amount 14`

`表示每天夜间12点半和中午12点半进行Cassandra数据库备份，并保存最新的14次备份`


以下命令会恢复指定的Cassandra数据库文件，在恢复数据库之前,系统会再次对当前的数据库进行备份。以防万一，建议用户对数据库再次备份。

` [root@ localhost ~]# zstack-ctl restore_cassandra -f cassandra-db.tgz`

`Stopping ZStack web UI, it may take a few minutes...`

`successfully stopped the UI server`

`Stopping ZStack management node, it may take a few minutes...`

`successfully stopped management node`

`Stopping kairosdb, it may take a few minutes...`

`successfully stopped kairosdb`

`Stopping cassandra, it may take a few minutes...`

`successfully stopped Cassandra`

`Restore cassandra keyspace zstack_billing successful from cassandra-db.tgz!`

`cassandra-db.tgz代表待恢复的cassandra数据库文件`




