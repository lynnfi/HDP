###csv导入hive中文乱码问题

改变该表的编码标准：(不推荐)
    
    ALTER TABLE company_listed SET SERDEPROPERTIES ('serialization.encoding'='GBK');
因为采用该种解决方案在Ambari页面上查询数据时并不能使用gbk编码显示中文，Ambari使用UTF-8进行编码。

建议采用以下解决方案：
如果是gbk格式的文件，使用sublime将csv文件转换utf-8格式。然后再导入hive表中。

1. 创建外部表
```
CREATE EXTERNAL TABLE test_100m(
     ip STRING, name STRING,
     logdate TIMESTAMP,log STRING COMMENT 'Access Log For the ip Address of the User')
 COMMENT 'This is the 100 million rows test table'
 ROW FORMAT DELIMITED FIELDS TERMINATED BY ','
 STORED AS TEXTFILE
 LOCATION '/apps/hive/warehouse/testdata';
```