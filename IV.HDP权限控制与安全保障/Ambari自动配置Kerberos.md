###使用Ambari自动配置Kerberos

1. 确认你已经安装了KDC并启动了KDC服务，确认你已经安装了JCE;

2. 登录到Ambari，在菜单栏中 Admin > Kerberos;

3. 点击 “Enable Kerberos”进入向导安装模式;

4. 选择你之前配置的KDC版本信息(我们之前配置的是MIT KDC);

5. 勾选选框确认已经完成了Kerberos安装前的准备事项;

6. 填写KDC相关配置信息(这里假设你已经按照我们之前的步骤安装了KDC)
   
     * **KDC**
       - KDC Host，可填写ip或者FQDN，端口号可填可不填
        
        `10.194.186.39`
       - Realm name，之前设置的域名
         
         `BMSOFT.COM`
       - (选填)Domains
       
         `bmsoft.com,bmsoft.com`
     * **Kadmin**
       -  Kadmin Host,可填写ip或者FQDN，端口号可填可不填
       
           `hdp39`
       - Admin principal & password，安装KDC服务器时创建的用户和密码
       
           Admin:`admin` &  PassWord:`bmsoft`
           
       - （选填）Save Admin Credentials,对证书进行加密
           
7. 根据你的环境进行Kerberos高级配置

8. 确认安装

9. Ambari 将会在所有的节点上安装Kerberos clients并在"testing"步骤中测试Ambari是否可以创建principal，生成keytab以及分发keytab

10. 确认安装信息，可以选择下载CSV文件
[a](/IV.HDP权限控制与安全保障/Kerberos安装与部署.md)


11. 继续安装操作，一路Next,然后Ambari会完成整个集群的Kerberied过程；（要是失败了记得多Retry几次，有时候脚本跑起来并不是很稳定~）

12. 最后Complete！（我看了一下手动部署Kerberos的过程，只能说感谢有Ambari，赶紧去github上给它加了个星）

  ![](/assets/KerberosComplete.jpeg)
