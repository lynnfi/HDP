###Flume导入HBase

使用Flume监控log日志，并将其导入HBase：

1. 进入Flume配置文件目录下
`cd /etc/flume/conf`

2. 创建Flume配置文件
`vi log2hbase.conf `
3. 在文件中添加以下内容：    

    ```
    a1.sources = r1
    
    a1.channels = c1
    
    a1.sources.r1.type = exec
    
    a1.sources.r1.command = tail -F /var/log/secure
    
    a1.sources.r1.channels = c1
    
    a1.channels = c1
    
    a1.channels.c1.type = memory
    
    a1.channels.c1.capacity = 10000
    
    a1.channels.c1.transactionCapacity = 10000
    
    a1.channels.c1.byteCapacityBufferPercentage = 20
    
    a1.channels.c1.byteCapacity = 800000
    
    a1.channels = c1
    
    a1.sinks = k1
    a1.sinks.k1.batchSize = 10
    
    a1.sinks.k1.type = hbase
    a1.sinks.k1.table = webservice_log
    a1.sinks.k1.columnFamily = cf_log
    
    a1.sinks.k1.serializer = org.apache.flume.sink.hbase.RegexHbaseEventSerializer
    a1.sinks.k1.serializer.rowKeyIndex = 0
    
    a1.sinks.k1.serializer.regex=^([^,]+),([^,]+),([^,]+),([^,]+)$
    a1.sinks.k1.serializer.colNames=c1,c2,c3,c4        
    a1.sinks.k1.channel = c1

    
    a1.sinks.k1.kerberosPrincipal = hbase/hdp40@BMSOFT.COM
    a1.sinks.k1.kerberosKeytab = /etc/security/keytabs/hbase.service.keytab 
        ```
        
4. 运行Flume客户端
    
    ```flume-ng agent -c /etc/flume/conf -f /etc/flume/conf/log2hbase.conf -Dflume.root.logger=DEBUG,console -n a1
    ```
    参数说明：
    -n 指定agent名称
    -c 指定配置文件目录
    -f 指定配置文件
    -Dflume.root.logger=DEBUG,console设置日志级别


