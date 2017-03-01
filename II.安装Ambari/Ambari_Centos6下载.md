###1.1 RHEL/CentOS/Oracle Linux 6

确认你将操作的主机能够连接到互联网，进入命令行并按一下步骤完成操作：

1. 以root身份登录到主机
    
        su root
2. 下载 Ambari repository文件到目标主机

        wget -nv http://public-repo-1.hortonworks.com/ambari/centos6/2.x/updates/2.4.2.0/ambari.repo -O /etc/yum.repos.d/ambari.repo
        
3. 确认主机的yum repository已经正确配置

        yum repolist
        
        