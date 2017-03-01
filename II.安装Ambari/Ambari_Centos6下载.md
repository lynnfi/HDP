### 1.1 RHEL/CentOS/Oracle Linux 6

确认你将操作的主机能够连接到互联网，进入命令行并按一下步骤完成操作：

1. 以root身份登录到主机

   ```
    su root
   ```

2. 下载 Ambari repository文件到目标主机

   ```
    wget -nv http://public-repo-1.hortonworks.com/ambari/centos6/2.x/updates/2.4.2.0/ambari.repo -O /etc/yum.repos.d/ambari.repo
   ```

3. 确认主机的yum repository已经正确配置

   ```
    yum repolist
   ```

   你应该能够看到与下表相似的Ambari repository 列表，其中各版本信息与所需安装的Ambari版本有关。

        

      | repo id |repo name  |status  |
      | :--- | :--- | :--- |
      | AMBARI.2.4.2.0-2.x | Ambari 2.x | 	5 | 
      |base  | CentOS-6 - Base |  6518|
      | extra |CentOS-6 - Extras  | 15 |
      |updates  | CentOS-6 - Updates | 209 |




