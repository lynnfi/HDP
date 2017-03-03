###使用Ambari自动配置Kerberos

1. 确认你已经安装了KDC并启动了KDC服务，确认你已经安装了JCE;

2. 登录到Ambari，在菜单栏中 Admin > Kerberos;

3. 点击 “Enable Kerberos”进入向导安装模式;

4. 选择你之前配置的KDC版本信息(我们之前配置的是MIT KDC);

5. 勾选选框确认已经完成了Kerberos安装前的准备事项;

6. 填写KDC相关配置信息(这里假设你已经按照我们之前的步骤安装了KDC)
   
     * **KDC**
       - KDC Host   ->10.194.186.39
       - Realm name  ->BMSOFT.COM
       - Domains field,
     * **Kadmin**