### Ranger安装前准备

Before you install Ranger, make sure your cluster meets the following requirements:

| ![](http://docs.hortonworks.com/HDPDocuments/HDP2/HDP-2.5.0/bk_security/common/images/admon/important.png "\[Important\]") | Important |
| :--- | :--- |
|  | As of HDP-2.5, Audit to DB is no longer supported. If you previously used Audit to DB, you can migrate the logs to Solr using the instructions in[Migrating Audit Logs from DB to Solr in Ambari Clusters](http://docs.hortonworks.com/HDPDocuments/HDP2/HDP-2.5.0/bk_security/content/migrating_audit_logs_from_db_to_solr_in_ambari_clusters.html). |



* It is recommended that you store audits in both HDFS and Solr. The default configuration for Ranger Audits to Solr uses the shared Solr instance provided under the[Ambari Infra](http://docs.hortonworks.com/HDPDocuments/Ambari-2.4.2.0/bk_ambari-user-guide/content/ch_ambari_infra.html)service. For more information about Audits to Solr, see[Ranger Audit Settings](http://docs.hortonworks.com/HDPDocuments/HDP2/HDP-2.5.0/bk_security/content/ranger_audit_settings.html)and[Using Apache Solr for Ranger Audits](http://docs.hortonworks.com/HDPDocuments/HDP2/HDP-2.5.0/bk_security/content/using_apache_solr_for_ranger_audits.html).

* To ensure that LDAP/AD group level authorization is enforced in Hadoop, you should[set up Hadoop group mapping](http://docs.hortonworks.com/HDPDocuments/HDP2/HDP-2.5.0/bk_security/content/setting_up_hadoop_group_mappping_for_ldap_ad.html)for LDAP.

* A MySQL, Oracle, or PostgreSQL database instance must be running and available to be used by Ranger.

  The Ranger installation will create two new users \(default names: rangeradmin and rangerlogger\) and two new databases \(default names: ranger and ranger\_audit\).

* Configuration of the database instance for Ranger is described in the following sections for some of the databases supported by Ranger.



  * [Configuring MySQL for Ranger](http://docs.hortonworks.com/HDPDocuments/HDP2/HDP-2.5.0/bk_security/content/configuring_mysql_for_ranger.html)

  * [Configuring PostgreSQL for Ranger](http://docs.hortonworks.com/HDPDocuments/HDP2/HDP-2.5.0/bk_security/content/configuring_postgresql_for_ranger.html)

  * [Configuring Oracle for Ranger](http://docs.hortonworks.com/HDPDocuments/HDP2/HDP-2.5.0/bk_security/content/configuring_oracle_for_ranger.html)

* If you choose not to provide system Database Administrator \(DBA\) account details to the Ambari Ranger installer, you can use the`dba_script.py`Python script to create Ranger DB database users without exposing DBA account information to the Ambari Ranger installer. You can then run the normal Ambari Ranger installation without specifying a DBA user name and password. For more information see[Setting up Database Users Without Sharing DBA Credentials](http://docs.hortonworks.com/HDPDocuments/HDP2/HDP-2.5.0/bk_security/content/setting_up_database_users_without_sharing_dba_credentials.html).



