## 一、本地源的准备

  下载 Ambari ：
  
 http://public-repo-1.hortonworks.com/ambari/centos6/2.x/updates/2.4.2.0/ambari-2.4.2.0-centos6.tar.gz



### 二、创建ambari目录并将源包解压到对应目录下

cd /var/www/html/ && mkdir ambari 

tar -vzxf ambari-2.4.2.0-centos6.tar.gz -C /var/www/html/ambari/AMBARI-2.4.2.0 

### 三、配置Ambari的本地源
      
     首先下载上面资源列表中的相应repo文件，修改其中的URL为本地源对应的地址

```
cd /etc/yum.repos.d/
 wget http://public-repo-1.hortonworks.com/ambari/centos6/2.x/updates/2.4.2.0/ambari.repo

修改 ambari.repo 
vi ambari.repo
 
 #VERSION_NUMBER=2.4.2.0-136

[Updates-ambari-2.4.2.0]
name=ambari-2.4.2.0 - Updates
baseurl=http://192.168.22.178/ambari/HDP/centos6/
gpgcheck=1
gpgkey=http://192.168.22.178/ambari/HDP/centos6/RPM-GPG-KEY/RPM-GPG-KEY-Jenkins
enabled=1
priority=1

```

### 四、安装Ambari
     ```
      通过yum安装ambari
      yum install ambari-server -y 

       配置Ambari
       ambari-server setup
  
      启动Ambari
       ambari-server start 
    
      通过界面访问ambari
     http://<your.ambari.server>:8080  
     ````