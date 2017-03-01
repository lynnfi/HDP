##JDK安装
1.下载jdk1.8安装包

2.配置环境变量
    
    vim /etc/profile
    在文件末尾添加:
    $JAVA_HOME=/usr/local/java/jdk1.8.0_121
    export PATH=$JAVA_HOME/bin:$PATH