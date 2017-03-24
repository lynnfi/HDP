###csv导入hive中文乱码问题

改变该表的编码标准即可：

ALTER TABLE company_listed SET SERDEPROPERTIES ('serialization.encoding'='GBK');
