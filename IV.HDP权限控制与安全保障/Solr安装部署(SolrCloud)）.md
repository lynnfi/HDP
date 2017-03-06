####Solr安装部署

* 配置需求

**Solr Prerequisites**

  * Ranger supports Apache Solr 5.2 or higher.

  * Apache Solr requires the Java Runtime Environment (JRE) version 1.7 or higher.

  
  * 1 TB free space in the volume where Solr will store the index data.


  * 32 GB RAM.


**SolrCloud Prerequisites**

  * SolrCloud supports replication and sharding. It is highly recommended that you use SolrCloud with at least two Solr nodes running on different servers with replication enabled.

  * SolrCloud requires Apache Zookeeper.

  * SolrCloud with Kerberos requires Apache Zookeeper and MIT Kerberos.