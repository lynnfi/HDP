##shell操作HBase

1. 创建表
创建test表，cf1,cf2为column family
```
create 'test',{NAME => 'cf1', VERSIONS => 2},{NAME => 'cf2', VERSIONS => 2}
```