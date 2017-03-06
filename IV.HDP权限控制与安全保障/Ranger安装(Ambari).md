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

4. 输入Kerberos的principle验证（一定要注意principle信息必须完整）  
   ![](/assets/ranger_kerberos.png)



