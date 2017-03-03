###Kerberos的安装与部署

1.安装最新版的KDC server
    
    yum install krb5-server krb5-libs krb5-workstation
    
2.编辑配置文件

    vi /etc/krb5.conf
    
3.修改[realms]选项中的相关配之信息