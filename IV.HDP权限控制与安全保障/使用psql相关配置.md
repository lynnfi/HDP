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

