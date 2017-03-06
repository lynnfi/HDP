####使用PostgreSQL的相关配置

因为Ranger的安装比较复杂，在使用到的关系型数据库上面，我们选择之前用作Ambari默认数据库的postgre；
以下是关于进行Ranger安装前的一些必要配置：

1. 确认postgres正在运行

        ps -eaf | grep ambari | grep postgres

2. 确认postgres的运行端口

        netstat -anp | grep ${pid}
        
3. 进入psql命令行
        
        sudo -u postgres psql -U postgres
        
4. 创建所需用户

        Create user rangerdba；
        ##设置密码
        ALTER USER rangerdba WITH PASSWORD "bmsoft"
        
5. 创建所需数据库

        CREATE DATABASE ranger OWNER rangerdba;
        
6. 设置远程连接权限

        vi  /var/lib/pgsql/data/postgresql.conf
        
        ####在连接设置处修改允许接入的客户端，*为所有连接   
        # - Connection Settings -
        listen_addresses = '*'        # what IP address(es) to listen on;
                                        # comma-separated list of addresses;
                                        # defaults to 'localhost', '*' = all

7.设置数据库访问权限

        vi  /var/lib/pgsql/data/pg_hba.conf
        
        ####在文件结尾处添加    
        local   all   postgres,rangerdba                       trust
        
        host   all   postgres,rangerdba          0.0.0.0/0                   trust
        
        host   all   postgres,rangerdba           ::/0                   trust

8. 刷新Postgres数据库
        
        sudo -u postgres /usr/bin/pg_ctl -D /var/lib/pgsql/data reload

9.确认postgresql的JDBC连接所需jar包
        ```
        yum install postgresql-jdbc*
        
        #确认已经安装好
        ls /usr/share/java/postgresql-jdbc.jar
        
        #修改文件权限
        chmod 644 /usr/share/java/postgresql-jdbc.jar
        
        #Ambari连接设置     
        ambari-server setup --jdbc-db=postgres --jdbc-driver=/usr/share/java/postgresql-jdbc.jar
        
        #修改HADOOP配置信息
        export HADOOP_CLASSPATH=${HADOOP_CLASSPATH}:${JAVA_JDBC_LIBS}:/connector jar path
        
        ```


