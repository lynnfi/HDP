##Hive开发指南
这里主要针对安装kerberos之后的Hive集群进行讲解，如果你想知道未安装kerberos的Hive应该如何进行开发可以直接bing，这里不做过多介绍。

*重要：

1. 初始化kerberos的ticket（如果不进行初始化，将不能够连接到Hiveserver，由于我们的kerberos才用的是keytab的认证方式，所以密码认证并不可行！）

        kinit -k -t /etc/security/keytabs/hive.service.keytab  hive/hdp40@BMSOFT.COM
        
2. 查看是否初始化成功
```

  $>  klist     
        
        Ticket cache: FILE:/tmp/krb5cc_0
        Default principal: hive/hdp40@BMSOFT.COM

        Valid starting     Expires            Service principal
        03/08/17 17:20:11  03/09/17 17:20:05  krbtgt/BMSOFT.COM@BMSOFT.COM
        renew until 03/08/17 17:20:11      
```

3. 连接beeline

```       
    $ > beeline
              !connect jdbc:hive2://10.194.186.40:10000/default;principal=hive/hdp40@BMSOFT.COM org.apache.hive.jdbc.HiveDriver

```

