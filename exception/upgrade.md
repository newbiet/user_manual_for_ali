# 22.1.2 升级异常处理

1. 请确保网络连接畅通，安装过程会使用在线安装源安装系统依赖。

2. 如果管理节点在升级前，因为异常导致关机，在升级时，可能遇到以下错误信息，“Reason: Database upgrading dry-run failed. You probably should use -F opto do force upgrading” 此时升级时，需要额外加入“-F”参数。

3. 出现以下错误信息时，“Reason: java-1.8.0-openjdk is not installed. Did you forget updating management node local repos to latest CentOS ZStack Community ISO? Please use following steps to update local repos”，请确保系统安装了最新可用的java1.8 版本，如果使用ZStack定制版安装的系统，可参考[22.12](/other-setting/upgrade-zstack-iso.md)升级ZStack定制版ISO的yum源后再升级云计算系统软件。

4. 升级错误会打印到屏幕上,可查看/tmp/zstack_installation.log，根据错误提示，尝试解决安装问题。也可将对应错误信息提交到Mevoco官网用户讨论组中获取更多帮助。

