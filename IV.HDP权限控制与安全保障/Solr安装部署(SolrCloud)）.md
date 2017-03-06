#### Solr安装部署

* 配置需求

  **Solr Prerequisites**

  * Ranger supports Apache Solr 5.2 or higher.

  * Apache Solr requires the Java Runtime Environment \(JRE\) version 1.7 or higher.

  * 1 TB free space in the volume where Solr will store the index data

  * 32 GB RAM.

  **SolrCloud Prerequisites**

  * SolrCloud supports replication and sharding. It is highly recommended that you use SolrCloud with at least two Solr nodes running on different servers with replication enabled

  * SolrCloud requires Apache Zookeeper.

  * SolrCloud with Kerberos requires Apache Zookeeper and MIT Kerberos.

\*



#### Installation and Configuration Steps


1. Run the following commands:

   ```
   cd $HOME
   git clone https://github.com/apache/incubator-ranger.git
   cd incubator-ranger/security-admin/contrib/solr_for_audit_setup
   ```

2. Edit the`install.properties`file \(see the instructions in the following sections\).

3. Run the`./setup.sh`script.

4. Refer to`$SOLR_RANGER_HOME/install_notes.txt`for additional instructions.



#### 1.2.2. Solr Installation

You can download the Solr package from[Apache Solr Downloads](http://lucene.apache.org/solr/downloads.html). Make sure that the Solr version is 5.2 or above. You can also use the Ranger`setup.sh`script to automatically download, install, and configure Solr. If you would like to use the setup.sh script to install Solr, set the following properties in the install.properties files, along with the settings from the one of the configuration options in the following sections.





**Table 5.1. Solr install.properties Values for setup.sh script**

| Property Name | Value | Description |
| :--- | :--- | :--- |
| SOLR\_INSTALL | true | When set to`true`, he`setup.sh`script will download the Solr package and install it. |
| SOLR\_DOWNLOAD\_URL | [http://archive.apache.org/dist/lucene/solr/5.2.1/solr-5.2.1.tgz](http://archive.apache.org/dist/lucene/solr/5.2.1/solr-5.2.1.tgz) | It is recommended that you use one for Apache mirror sitess to download the Solr package. You can choose a mirror site at[http://lucene.apache.org/solr/mirrors-solr-latest-redir.html](http://lucene.apache.org/solr/mirrors-solr-latest-redir.html) |
| SOLR\_INSTALL\_FOLDER | /opt/solr | The Solr install folder. |

####安装部署
1. 运行以下命令：

  ```
  yum install lucidworks-hdpsearch
  
  注:solr将会被安装到 /opt/lucidworks-hdpsearch/solr
  ```
  
2. 设置solrcloud：
 ``` 
  vi install.properties
  
  #设置JAVA_HOME
    JAVA_HOME=/usr/local/java/jdk1.8.0_121
  #NOTE:设置SOLR_INSTALL为false
    SOLR_INSTALL=false
  #设置SOLR_RANGER_HOME
    SOLR_RANGER_HOME=/opt/solr/ranger_audit_server
  #设置SOLR_RANGER_PORT
    SOLR_RANGER_PORT=8886
  #设置"standalone" or "solrcloud"
    SOLR_DEPLOYMENT=solrcloud 
  #设置SOLR_ZK
    SOLR_ZK=10.194.186.41:2181/ranger_audits,hdp39:2181/ranger_audits,hdp40:2181/ranger_audits
  #设置SOLR_MAX_MEM
    SOLR_MAX_MEM=1g
  ```
3. 运行./setup.sh
    
        ./setup.sh
  
 
4. 每个节点仅运行一次
    
        /opt/solr/ranger_audit_server/scripts/add_ranger_audits_conf_to_zk.sh
        
        
5. Create Ranger Audit collection: /opt/solr/ranger_audit_server/scripts/create_ranger_audits_collection.sh

