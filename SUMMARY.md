# Summary

* [本书简介](README.md)

## HDP安装指南

* [I.安装前准备](I.安装前准备/I.安装前准备.md)
  * [1. 基本认知](I.安装前准备/基本概念.md)
  * [2. 部署方案确认](I.安装前准备/部署方案确认.md)
  * [3. 最低资源需求](I.安装前准备/最低资源需求.md)
    * [3.1 操作系统需求](I.安装前准备/操作系统需求.md)
    * [3.2 浏览器需求](I.安装前准备/浏览器需求.md)
    * [3.3 软件版本需求](I.安装前准备/浏览器版本需求.md)
    * [3.4 JDK版本需求](I.安装前准备/JDK需求.md)
    * [3.5 数据库需求](I.安装前准备/数据库需求.md)
    * [3.6 内存需求](I.安装前准备/内存需求.md)
    * [3.7 安装包大小与节点](I.安装前准备/安装包大小与节点数.md)
    * [3.8 最大打开文件数设置](I.安装前准备/最大打开文件数设置.md)
  * [4.系统环境配置](I.安装前准备/系统环境配置.md)
    * [4.1 检查DNS和NSCD设置](I.安装前准备/检查DNS和NSCD设置.md)
      * [4.1.1 编辑host文件](I.安装前准备/编辑host文件.md)
      * [4.1.2 设置hostname](I.安装前准备/编辑hostname文件.md)
      * [4.1.3 设置network文件](I.安装前准备/设置network文件.md)
    * [4.2 安装JDK与JCE](I.安装前准备/安装JDK与JCE.md)
    * [4.3 ssh无密码登录](I.安装前准备/ssh无密码登录.md)
    * [4.4 ntp时间同步](I.安装前准备/ntp时间同步.md)
    * [4.5 关闭防火墙](I.安装前准备/关闭防火墙.md)
    * [4.6 禁用SELinux和PackageKit](I.安装前准备/禁用SELinux&PackageKit.md)
    * [4.7 Python2.7配置](I.安装前准备/Python2.7配置.md)    
* [II.安装Ambari](II.安装Ambari/安装Ambari.md)
  * [5. 通过yum安装Ambari](II.安装Ambari/下载Ambari安装包.md)
    * [5.1 RHEL/CentOS/Oracle Linux 6](II.安装Ambari/Ambari_Centos6下载.md)
    * [5.2 RHEL/CentOS/Oracle Linux 7](II.安装Ambari/Ambari_Centos7下载.md)
  * [6. 配置Ambari Server](II.安装Ambari/配置AmbariServer.md)
* [III.安装、配置并部署HDP集群](III.部署HDP集群/HDP集群部署.md)
  * [7. 登录并简单了解Ambari](III.部署HDP集群/下载Ambari安装包.md)
  * [8. HDP集群搭建](III.部署HDP集群/HDP集群搭建.md)
    * [8.1 为HDP集群命名](III.部署HDP集群/HDP集群命名.md)
* [IV.HDP权限控制与安全保障](IV.HDP权限控制与安全保障/HDP权限控制与安全保障.md)
  * [1. Kerberos安装与部署](IV.HDP权限控制与安全保障/Kerberos安装与部署.md)
    * [1.1 安装KDC服务器](IV.HDP权限控制与安全保障/安装KDC服务器.md)
    * [1.2 使用Ambari自动配置Kerberos](IV.HDP权限控制与安全保障/Ambari自动配置Kerberos.md)
    * [1.3 配置Ambari管理Kerberos鉴权](IV.HDP权限控制与安全保障/配置Ambari管理Kerberos鉴权.md)
    * [1.4 配置ticket有效时间](IV.HDP权限控制与安全保障/配置ticket有效时间.md)
  * [2. Ranger的安装与部署](IV.HDP权限控制与安全保障/Ranger安装与部署.md)
    * [2.1 Ranger安装前准备](IV.HDP权限控制与安全保障/Ranger安装前准备.md)
      * [2.1.1 Solr安装部署\(SolrCloud\)](IV.HDP权限控制与安全保障/Solr安装部署%28SolrCloud%29）.md)
      * [2.1.2 PostgreSQL相关配置](IV.HDP权限控制与安全保障/使用psql相关配置.md)
    * [2.2 Ranger安装\(Ambari\)](IV.HDP权限控制与安全保障/Ranger安装.md)
    * [2.3 启用个组件的Ranger插件\(Ambari\)](IV.HDP权限控制与安全保障/启用个组件的Ranger插件.md)
  * [3. Knox的安装与部署](IV.HDP权限控制与安全保障/Knox安装与部署.md)
    * [3.1 安装Knox服务](IV.HDP权限控制与安全保障/3.1Knox安装与部署.md)
* [V.HDP单点登录与网关](V.HDP单点登录与网关/HDP单点登录与网关.md)
  * [1.1 使用LDAP实现统一用户管理](V.HDP单点登录与网关/使用LDAP实现统一用户管理.md)
    * [1.1.1 Ambari统一用户管理配置](V.HDP单点登录与网关/Ambari统一用户管理配置.md)
    * [1.1.2 Ranger统一用户管理配置](V.HDP单点登录与网关/Ranger统一用户管理配置.md)
  * [1.2 使用Knox实现单点登录](V.HDP单点登录与网关/使用Knox实现单点登录.md)

## HDP产品描述

* [VI.用户与数据权限管理指南](V.用户与数据权限管理指南/Ranger使用指南.md)
  * [1. Ranger对各组件数据权限管理](V.用户与数据权限管理指南/Ranger对各组件的数据权限管理.md)
    * [1.1 HDFS数据权限管理](V.用户与数据权限管理指南/HDFS数据权限管理.md)
  * [2. Yarn实现多租户管理](V.用户与数据权限管理指南/Yarn实现多租户管理.md)

## HDP应用开发指南

* [VII.HDP应用开发指南](VI.HDP应用开发指南/应用开发指南.md)
  * [1.Hive开发指南](VI.HDP应用开发指南/Hive开发指南.md)
    * [1.1Hive\_JDBC开发示例](VI.HDP应用开发指南/Hive_JDBC开发指南.md)
    * [1.2Csv导入Hive中文乱码问题解决](VI.HDP应用开发指南/csv导入Hive乱码问题解决.md)

## 附录

* [附录I.常用工具](附录I.常用工具/常用工具.md)
  * [1.LDAP管理软件](附录I.常用工具/LDAP管理工具.md)

