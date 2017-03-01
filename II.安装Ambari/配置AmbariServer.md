##2.配置Ambari Server


在启动 Ambari Server之前, 你 **必须** 先设置Ambari Server. 设置操作将会包含，Ambari使用的database, JDK并且允许你配置用户已经在使用的数据库或JDK版本。

运行以下命令，按照提示进行配置操作。你也可以参考setup常用可选[指令](II.安装Ambari/Setup常用指令.md)：

    ambari-server setup
    
    #是否自定义用户运行Ambari守护进程（否）
    Customize user account for ambari-server daemon [y/n] (n)? 
    
    #JDK版本选择，直接选择【3】，用户自定义JDK版本
    Checking JDK...
    [1] Oracle JDK 1.8 + Java Cryptography Extension (JCE) Policy Files 8
    [2] Oracle JDK 1.7 + Java Cryptography Extension (JCE) Policy Files 7
    [3] Custom JDK
    ==============================================================================
    Enter choice (1): 3
    
    #将本机的$JAVA_HOME路径设置过来，且要确保其他客户机的JAVA_HOME也是这个路径
    Path to JAVA_HOME: /usr/local/java/jdk1.8.0_121
    
    #进入数据库高级设置？（否）
    Enter advanced database configuration [y/n] (n)? 
    这里如果选择是，将可以自定义数据库配置，默认为PostgreSql，用户名:ambari,密码:bigdata
    



配置提示：

    1. If you have not temporarily disabled SELinux, you may get a warning. Accept the default (y), and continue.

    2. By default, Ambari Server runs under root. Accept the default (n) at the Customize user account for ambari-server daemon prompt, to proceed as root. If you want to create a different user to run the Ambari Server, or to assign a previously created user, select y at the Customize user account for ambari-server daemon prompt, then provide a user name. Refer to the Hortonworks Data Platform Apache Ambari Reference > Configuring Ambari for Non-Root, for more information about running the Ambari Server as non-root.
    
    3. If you have not temporarily disabled iptables you may get a warning. Enter y to continue.

    4. Select a JDK version to download. Enter 1 to download Oracle JDK 1.8. Alternatively, you can choose to enter a Custom JDK. If you choose Custom JDK, you must manually install the JDK on all hosts and specify the Java Home path.