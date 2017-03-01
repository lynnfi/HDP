##JDK安装
_如果你需要使用Kerberos进行Hadoop的集群管理，你可能需要同时下载[JCE8](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html)_


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

*注：你可以先不去管Kerberos的事情，我们会有专门的一个版块来讲解配置Kerberos的事项。

