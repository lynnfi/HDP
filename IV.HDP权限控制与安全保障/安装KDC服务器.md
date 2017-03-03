###Kerberos的安装与部署

* 安装KDC Server

    1. 安装最新版的KDC server
        
            yum install krb5-server krb5-libs krb5-workstation
        
    2. 编辑配置文件
    
            vi /etc/krb5.conf
        
    3. 修改配置文件中的[realms]信息
        
            #将kdc与admin_server修改为主机地址(FQDN)
            
            [realms]
             EXAMPLE.COM = {
               kdc = 10.194.186.39
               admin_server = hdp39
            }
    4. 修改配置文件中的[libdefaults]信息
    
            #由于一些应用需要刷新tickets(如HUE)，所以进行如下设置：
            renew_lifetime = 7d