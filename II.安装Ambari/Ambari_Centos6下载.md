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

   | repo id | repo name | status |
   | :--- | :--- | :--- |
   | AMBARI.2.4.2.0-2.x | Ambari 2.x | 5 |
   | base | CentOS-6 - Base | 6518 |
   | extras | CentOS-6 - Extras | 15 |
   | updates | CentOS-6 - Updates | 209 |

4. 安装Ambari

   ```
     yum install ambari-server
   ```

5. 根据提示完成安装（输入y进行操作和版本信息的确认）

   安装成功后应该有如下输出：

   ```
   Installing : postgresql-libs-8.4.20-3.el6_6.x86_64         1/4
   Installing : postgresql-8.4.20-3.el6_6.x86_64              2/4
   Installing : postgresql-server-8.4.20-3.el6_6.x86_64       3/4
   Installing : ambari-server-2.4.2.0-1470.x86_64               4/4
   Verifying  : ambari-server-2.4.2.0-1470.x86_64               1/4
   Verifying  : postgresql-8.4.20-3.el6_6.x86_64              2/4
   Verifying  : postgresql-server-8.4.20-3.el6_6.x86_64       3/4
   Verifying  : postgresql-libs-8.4.20-3.el6_6.x86_64         4/4

   Installed:
     ambari-server.x86_64 0:2.4.2.0-1470

   Dependency Installed:
    postgresql.x86_64 0:8.4.20-3.el6_6           
    postgresql-libs.x86_64 0:8.4.20-3.el6_6        
    postgresql-server.x86_64 0:8.4.20-3.el6_6

   Complete!
   ```



