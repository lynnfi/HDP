####Kerberos的票据管理
在使用kerberos进行HDP集群安全认证的时候，我们需要对能够接入集群的用户进行管理，这个时候会需要使用到一些常用的命令。本小节将集中讲解如何管理kerberos的票据，包括生成、分发、删除等操作。

1. 登录 kerberos 

     $ /usr/sbin/kadmin.local   
     
2. 查看用户
     
     kadmin.local   ： listprincs
     
3. 添加用户

     kadmin.local   ： addprinc project2/hdp39@BMSOFT.COM
     
4. 删除用户
     
     kadmin.local   ： delprinc project2/hdp39@BMSOFT.COM

6. 创建keytable文件  生成 kadmin/admin kadmin/changepw 两个用户的 keytab 文件到 krb5kdc 目录

     kadmin.local ：ktadd -k /opt/keystore/project2.keytab project2/hdp39

