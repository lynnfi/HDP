### 通过Ambari启用各组件的Ranger插件

1. Ranger工作原理
   ![](/assets/Ranger_work.png)

2.Ranger组件介绍

| Component | Description |
| :--- | :--- |
| Ranger admin portal | The Ranger Admin portal is the central interface for security administration. Users can create and update policies, which are then stored in a policy database. Plugins within each component poll these policies at regular intervals. The portal also consists of an audit server that sends audit data collected from the plugins for storage in HDFS or in a relational database. |
| Ranger plugins | Plugins are lightweight Java programs which embed within processes of each cluster component. For example, the Apache Ranger plugin for Apache Hive is embedded within Hiveserver2. These plugins pull in policies from a central server and store them locally in a file. When a user request comes through the component, these plugins intercept the request and evaluate it against the security policy. Plugins also collect data from the user request and follow a separate thread to send this data back to the audit server. |
| User group sync | Apache Ranger provides a user synchronization utility to pull users and groups from Unix or from LDAP or Active Directory. The user or group information is stored within Ranger portal and used for policy definition. |



