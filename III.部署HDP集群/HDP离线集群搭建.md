9.1 安装HDP 前先安装Ambari-agent

9.11  提前手动安装ambari-agent：（每一节点都安装）

- 在其中一个节点上下载

  cd /etc/yum.repos.d/

 wget  http://public-repo-1.hortonworks.com/ambari/centos6/2.x/updates/2.4.2.0/ambari.repo

     并将其baseUrl修改为hdp源路径



9.12   安装ambari-agent

    yum install ambari-agent 

_修改ambari-agent.ini中要连接的主机名，这里每一个节点都是为了与安装ambari的主机进行连接，因此每个节点都应将hostname配置成ambari所对应的主机机名

如下所示： 

     vi /etc/ambari-agent/conf/ambari-agent.ini
    [server]
    hostname=hdp04.gzbigdata.org.cn
    url_port=8440
    secured_url_port=8441

9.13  启动ambari-agent

    ambari-agent start



9.2  HDP 离线安装

9.21  地源的准备

  HDP 、HDP-UTILS 源包（文件很大，需要很长下载时间，请耐心等待。。。），下载路径如下：

http://public-repo-1.hortonworks.com/HDP/centos6/2.x/updates/2.5.3.0/HDP-2.5.3.0-centos6-rpm.tar.gz

http://public-repo-1.hortonworks.com/HDP-UTILS-1.1.0.21/repos/centos6/HDP-UTILS-1.1.0.21-centos6.tar.gz 



9.22  源包解压到对应目录下

    目录不存在则先创建目录
    
    cd /var/www/html/ambari 
    
    tar -vzxf HDP-2.5.3.0-centos6-rpm.tar.gz -C /var/www/html/ambari/HDP
    tar -vzxf  HDP-UTILS-1.1.0.21-centos6.tar.gz -C /var/www/html/ambari/hdp-util

- 注：上述文件解压出来的文件可能与官方文档解压出来的目录有所不一样，但这并不会影响到正常安装



9.23  配置HDP、HDP-UTILS的本地源

    首先下载上面资源列表中的相应repo文件，修改其中的URL为本地的地址，相关配置如下
    相关文件下载路径为：

    cd /etc/yum.repos.d/
    
     [ http://public-repo-1.hortonworks.com/HDP/centos6/2.x/updates/2.5.3.0/hdp.repo ](http://note.youdao.com/)

- 修改 hdp.repo 

    vi HDP.repo
    [HDP-2.5]
    name=HDP-2.5
    baseurl=http://10.194.11.4/hdp/HDP/centos6/
    
    path=/
    enabled=1
    gpgcheck=0

- 修改 HDP-UTILS.repo

    vi HDP-UTILS.repo
    [HDP-UTILS-1.1.0.21]
    name=HDP-UTILS-1.1.0.21
    baseurl=http://10.194.11.4/hdp/HDP-UTILS-1.1.0.21/repo/centos6
    
    path=/
    enabled=1



9.24   安装HDP

Log In to Apache Ambari

http://<your.ambari.server>:8080 

- Install Options 这一步：
  虽然我们已经手动安装 ambari-agent 但依然可以选择通过 私钥的方式进行安装，因为yum方式在进行安装时会先自行检测要安装的组件是否已安装
  select Provide your SSH Private Key
  将id_rsa 输入
- 通过Web Ui 根据提示安装便可，在安装时注意选择本地源的安装方式。

如下图所示：
![](/assets/1.png)

在配置baseUrl 时路径得与hdp.repo中给的一致，不一定跟官方的一致，例如官方的hdp-utils的路径如下：http://<web.server>/hdp/HDP-UTILS-<version>/repos/<OS> ，但是我们解压出来的并不是这样，而是没有对应的的<OS>，但这并不影响安装。

baseurl=http://10.194.11.4/hdp/HDP/centos6/ 

注：参考官方文档

https://docs.hortonworks.com/HDPDocuments/Ambari-2.4.2.0/bk_ambari-installation/content/using_a_local_repository.html 

https://docs.hortonworks.com/HDPDocuments/Ambari-2.4.2.0/bk_ambari-installation/content/name_your_cluster.html 


