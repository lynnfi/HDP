####HDFS常用操作

1. 新建文件夹

        在hive的文件夹下面建立我们用于测试的数据文件夹"testdata"
        hdfs dfs -mkdir /apps/hive/warehouse/testdata
        
2. 导入本地文件到hdfs
        
         #使用hive用户
         su hive
         #初始化kerberos证书
         kinit -k -t /etc/hive/conf/hive.keytab hive/hdp39@BMSOFT.COM
         #导入我们准备好的文件
         hdfs dfs -put /bigdata/testdata/*.log /apps/hive/warehouse/testdata

