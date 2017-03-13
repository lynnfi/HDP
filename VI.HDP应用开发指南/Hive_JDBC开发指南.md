###Hive_JDBC开发指南

**1. 开发前准备**
    * 集成开发环境：Eclipse/IDEA
    * JAVA版本：jdk1.8+
    * Maven版本:3.0+


**2. 简单示例**
    * 新建Maven Project
    
    * 引入Maven依赖（Hive相关的依赖包都需要引进来）      
```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.bmsoft</groupId>
    <artifactId>hive</artifactId>
    <version>1.0-SNAPSHOT</version>

    <dependencies>
        <!-- https://mvnrepository.com/artifact/org.apache.hive/hive-jdbc -->
        <dependency>
            <groupId>org.apache.hive</groupId>
            <artifactId>hive-jdbc</artifactId>
            <version>1.2.1</version>
        </dependency>
        <!-- https://mvnrepository.com/artifact/org.apache.hadoop/hadoop-common -->
        <dependency>
            <groupId>org.apache.hadoop</groupId>
            <artifactId>hadoop-common</artifactId>
            <version>2.7.1</version>
        </dependency>
        <!-- https://mvnrepository.com/artifact/org.apache.hive/hive-exec -->
        <dependency>
            <groupId>org.apache.hive</groupId>
            <artifactId>hive-exec</artifactId>
            <version>1.2.1</version>
        </dependency>
        <!-- https://mvnrepository.com/artifact/org.apache.hive/hive-metastore -->
        <dependency>
            <groupId>org.apache.hive</groupId>
            <artifactId>hive-metastore</artifactId>
            <version>1.2.1</version>
        </dependency>
        <!-- https://mvnrepository.com/artifact/org.apache.hive/hive-common -->
        <dependency>
            <groupId>org.apache.hive</groupId>
            <artifactId>hive-common</artifactId>
            <version>1.2.1</version>
        </dependency>
        <!-- https://mvnrepository.com/artifact/org.apache.hive/hive-service -->
        <dependency>
            <groupId>org.apache.hive</groupId>
            <artifactId>hive-service</artifactId>
            <version>1.2.1</version>
        </dependency>
    </dependencies>
</project>
```

* 示例程序HiveSimple.java
```
package com.bmsoft.hive;

/**
 * Created by chentao on 10/03/2017.
 */
import org.apache.hadoop.security.UserGroupInformation;
import org.apache.hive.jdbc.HiveDriver;

import java.io.IOException;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import org.apache.log4j.Logger;
/**
 * 2017-03-08 20:07:50
 * @author chentao
 *简单的jdbc连接hive实例（已开启kerberos服务）
 */


public class HiveSimple {

    private static String driverName = "org.apache.hive.jdbc.HiveDriver";
    private static String url = "jdbc:hive2://10.194.186.40:10000/default;principal=hive/hdp40@BMSOFT.COM";
    private static String user = "";
    private static String password = "";
    private static String sql = "";
    private static ResultSet res;


    public static void main(String[] args) {
		org.apache.hadoop.conf.Configuration conf = new  org.apache.hadoop.conf.Configuration();
        conf.set("hadoop.security.authentication", "Kerberos");
        try {
            UserGroupInformation.setConfiguration(conf);
            UserGroupInformation.loginUserFromKeytab("hive/hdp39@BMSOFT.COM", "/Users/chentao/Desktop/hive.keytab");
		} catch (IOException e1) {
			// TODO Auto-generated catch block
			e1.printStackTrace();
		}

        try {
            Class.forName(driverName);
            Connection conn = DriverManager.getConnection(url);
            Statement stmt = conn.createStatement();

            // 创建的表名
            String tableName = "testHiveDriverTable";

            /** 第一步:存在就先删除 **/
            //sql = "DROP TABLE IF EXISTS" + tableName;
            // stmt.executeQuery(sql);

            /** 第二步:不存在就创建 **/
            stmt.execute("create table " + tableName + "(key int, value string)");

        //查看数据库下所有的表
            sql = "show tables";
            System.out.println("Running:" + sql);
            res = stmt.executeQuery(sql);
            System.out.println("执行“show tables”运行结果:");
            while (res.next()) {
                System.out.println(res.getString(1));
            }

            conn.close();
        } catch (SQLException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        } catch (ClassNotFoundException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }finally{
            System.out.println("!!!!!!END!!!!!!!!");
        }
    }
}
```
