###csv导入hive中文乱码问题

ALTER TABLE company_listed SET SERDEPROPERTIES ('serialization.encoding'='GBK');
