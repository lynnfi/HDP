### Ranger安装

1. 登录Ambari，Dashboard&gt;&gt;Actions&gt;&gt;Add Service  
   ![](/assets/findRanger.png)

2. 确认完成了安装前配置  
   ![](/assets/rangerEnsure.png)

3. 配置Ranger安装所需数据库信息

   ```
   Ranger DB name: ranger
   Ranger DB host: hdp39
   Ranger DB username: rangerdba
   Ranger DB password: bmsoft
   ```

   ![](/assets/rangerPostgre.png)

4. Ranger-Audit所需设置

   ```
   Audit to Solr>>SolorCloud
   #下面会自动填上，其实就是zookeeper的信息   
   ```

   ![](/assets/rangerAudit.png)

5. 输入Kerberos的principle验证（一定要注意principle信息必须完整）  
   ![](/assets/ranger_kerberos.png)

6. 一路Next没有什么大问题了

7. 完成后重启被影响到的组件  
   ![](/assets/restartCompents.png)

8. 登录Ranger\(http://10.194.186.41:6080\)  
   ![](/assets/rangerHome.png)



