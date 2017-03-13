##Hive开发指南
这里主要针对安装kerberos之后的Hive集群进行讲解，如果你想知道未安装kerberos的Hive应该如何进行开发可以直接bing，这里不做过多介绍。

*重要：

1.  远程连接安装有hiveClient的主机
        
        ssh 10.194.186.39

2. 初始化kerberos的ticket（如果不进行初始化，将不能够连接到Hiveserver，由于我们的kerberos才用的是keytab的认证方式，所以密码认证并不可行！）

        kinit -k -t /etc/security/keytabs/hive.service.keytab  hive/hdp39@BMSOFT.COM
        
3. 查看是否初始化成功(如果不成功换一台机器试一下)
```

  $>  klist     
        
        Ticket cache: FILE:/tmp/krb5cc_0
        Default principal: hive/hdp39@BMSOFT.COM

        Valid starting     Expires            Service principal
        03/08/17 17:20:11  03/09/17 17:20:05  krbtgt/BMSOFT.COM@BMSOFT.COM
        renew until 03/08/17 17:20:11      
```

4. 连接beeline,测试连接是否可用
```
    $ > beeline
         !connect jdbc:hive2://10.194.186.40:10000/default;principal=hive/hdp40@BMSOFT.COM org.apache.hive.jdbc.HiveDriver            
```

