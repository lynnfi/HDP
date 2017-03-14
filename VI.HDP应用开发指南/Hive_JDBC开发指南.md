###Hive_JDBC开发指南

####1. 整体流程
    1. 通过大数据授权中心获得一份kerberos认证所需keytab文件，./conf/hive.keytab

    1. 通过资源目录确认自己需要的信息，
    2. 确认自己对数据的访问权限，如果没有权限则申请权限
    3. 完成权限获取，开始进行数据操作~

####2. 开发前准备
    * 集成开发环境：Eclipse/IDEA
    * JAVA版本：jdk1.8+
    * Maven版本:3.0+
    * 获取kerberos认证所需keytab,并存放在开发路径下./conf/hive.keytab

####3. 简单示例
    * 新建Maven Project
    
    * 在pom.xml中引入以下Maven依赖（Hive相关的依赖包都需要引进来）      
```
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
        private static String sql = "";
        private static ResultSet res;
    
        public static void main(String[] args) {
            /**使用Hadoop安全登录**/
            org.apache.hadoop.conf.Configuration conf = new  org.apache.hadoop.conf.Configuration();
            conf.set("hadoop.security.authentication", "Kerberos");
            try {
                UserGroupInformation.setConfiguration(conf);
                UserGroupInformation.loginUserFromKeytab("hive/hdp39@BMSOFT.COM", "./conf/hive.keytab");
            } catch (IOException e1) {
                // TODO Auto-generated catch block
                e1.printStackTrace();
            }
            try {
                Class.forName(driverName);
                Connection conn = DriverManager.getConnection(url);
                Statement stmt = conn.createStatement();
                // 创建的表名
                String tableName = "page_view";
                /** 创建表 **/
                sql = "CREATE TABLE IF NOT EXISTS "+tableName+"(viewTime INT, userid BIGINT," +
                        "     page_url STRING, referrer_url STRING," +
                        "     ip STRING COMMENT 'IP Address of the User')" +
                        " COMMENT 'This is the page view table'" +
                        " PARTITIONED BY(dt STRING, country STRING)" +
                        " STORED AS SEQUENCEFILE";
                stmt.execute(sql);
                show_tables(stmt);
                /** 删除表**/
                drop_table(stmt,tableName);
                show_tables(stmt);
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
    
        /**
         * 查看数据库下所有的表
         * @param statement
         * @return
         */
        public static boolean show_tables(Statement statement){
            sql = "SHOW TABLES";
            System.out.println("Running:" + sql);
            try {
                res = statement.executeQuery(sql);
                System.out.println("执行“+sql+运行结果:");
                while (res.next()) {
                    System.out.println(res.getString(1));
                }
                return true;
            } catch (SQLException e) {
                e.printStackTrace();
            }
            return false;
        }
    
        /**
         *
         * @param statement
         * @param tableName
         * @return
         */
        public static boolean drop_table(Statement statement,String tableName){
            sql = "DROP TABLE IF EXISTS "+tableName;
            System.out.println("Running:" + sql);
            try {
                statement.execute(sql);
                System.out.println(tableName+"删除成功");
                return true;
            } catch (SQLException e) {
                System.out.println(tableName+"删除失败");
                e.printStackTrace();
            }
            return false;
        }
    }
```
