##shell操作HBase

1. 启动HBase shell
    * 初始化kerberos安全证书
        
        `kinit -k -t /etc/security/keytabs/hbase.service.keytab hbase/hdp39@BMSOFT.COM`
        
    * 启动HBase
    `HBase shell`

1. 创建表
创建test表，cf1,cf2为column family
```
create 'test',{NAME => 'cf1', VERSIONS => 2},{NAME => 'cf2', VERSIONS => 2}
```

2. 插入数据
    * 插入单行数据`put 'test','row1','cf1:c1','value1'`
    其中，test为表名,row1为行键值，cf1:c1为列族:列名，value1为值

2. 查看表数据
    
    * 查看全表数据
`scan test`
    * 根据rowkey获取单行数据`get 'test','row1'`