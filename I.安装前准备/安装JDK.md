##JDK安装
_如果你需要使用Kerberos进行Hadoop的集群管理，你可能需要同时下载[JCE8]()_


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

*注：
你可以先不去管Kerberos的事情，我们会有专门的一个版块来讲解配置Kerberos的事项，或者你可以先参考：[Hortonworks关于Kerberos的文档](http://docs.hortonworks.com/HDPDocuments/Ambari-2.4.2.0/bk_ambari-security/content/distribute_and_install_the_jce.html)

###安装JCE
_因为该版本会用到Kerberos进行Hadoop集群的安全保障，所以将会在此阶段配置JCE_

1. 下载JCE安装包
        - [JCE7](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html)(For JDK1.7)
        - [JCE8](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html)(For JDK1.8)

2. 将安装包解压到指定路径($JAVA_HOME/jre/lib/security/)

        
        unzip -o -j -q jce_policy-8.zip -d /usr/jdk64/jdk1.8.0_60/jre/lib/security/
