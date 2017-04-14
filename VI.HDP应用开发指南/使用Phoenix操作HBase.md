###使用Phoenix操作HBase

1. 启动Phoenix
    * 初始化kerberos安全证书
    
    `kinit -k -t /etc/security/keytabs/hbase.service.keytab hbase/hdp39@BMSOFT.COM`
    
    * 启动Phoenix
    
    ` /usr/hdp/current/phoenix-client/bin/sqlline.py hdp39:2181`
    
    * 参数说明：
    `hdp39:2181为zookeeper主机地址:端口号`
    
2. HBase查看操作

    * Phoenix语法参考：http://phoenix.apache.org/language/index.html
    
    2.1 查看数据库表：
    ```
    !table
    +------------+--------------+-------------+---------------+----------+---------+
| TABLE_CAT  | TABLE_SCHEM  | TABLE_NAME  |  TABLE_TYPE   | REMARKS  | TYPE_NA |
+------------+--------------+-------------+---------------+----------+---------+
|            | SYSTEM       | CATALOG     | SYSTEM TABLE  |          |         |
|            | SYSTEM       | FUNCTION    | SYSTEM TABLE  |          |         |
|            | SYSTEM       | SEQUENCE    | SYSTEM TABLE  |          |         |
|            | SYSTEM       | STATS       | SYSTEM TABLE  |          |         |
+------------+--------------+-------------+---------------+----------+---------+
    
    ```
    2.2 查看表结构
    ```
    !describe "STATS"
    
    +------------+--------------+-------------+-------------------------+----------+
| TABLE_CAT  | TABLE_SCHEM  | TABLE_NAME  |       COLUMN_NAME       | DATA_TYP |
+------------+--------------+-------------+-------------------------+----------+
|            | SYSTEM       | STATS       | PHYSICAL_NAME           | 12       |
|            | SYSTEM       | STATS       | COLUMN_FAMILY           | 12       |
|            | SYSTEM       | STATS       | GUIDE_POST_KEY          | -3       |
|            | SYSTEM       | STATS       | GUIDE_POSTS_WIDTH       | -5       |
|            | SYSTEM       | STATS       | LAST_STATS_UPDATE_TIME  | 91       |
|            | SYSTEM       | STATS       | GUIDE_POSTS_ROW_COUNT   | -5       |
+------------+--------------+-------------+-------------------------+----------+
    ```
    2.3 查看表内容
    
```
 select * from "STATS";
```
3. HBase新建操作

    * 新建HBase表
    ```
    CREATE TABLE test25 ( id BIGINT not null primary key, i.name VARCHAR(5) , i.phone BIGINT, i.addr VARCHAR, i.class DECIMAL(4)); 
UPSERT INTO TEST25 VALUES(99999,'foo',126548568,'bar',3); 
    ``` 
    
    
