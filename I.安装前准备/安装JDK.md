##JDK安装
1. 下载jdk1.8安装包

2. 将文件传到指定目录

        scp ~/Desktop/jdk-8u121-linux-x64.tar.gz root@10.194.168.11:/usr/local/java

3. 解压文件
        
        tar -zxvf jdk-8u121-linux-x64.tar.gz 
4. 配置环境变量
    
            vim /etc/profile
            在文件末尾添加:
            $JAVA_HOME=/usr/local/java/jdk1.8.0_121
            export PATH=$JAVA_HOME/bin:$PATH