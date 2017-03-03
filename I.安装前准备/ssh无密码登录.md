###ssh无密码登录
* 使用ssh命令完成无密码登录操作
    - 本机登录
	
          $ ssh-keygen -t rsa -P '' -f ~/.ssh/id_rsa 
          $ cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys

    - 远程登录（将公钥发送到需要无密码登录的目标节点）
			
           ssh-copy-id -i ~/.ssh/id_rsa.pub root@172.16.248.217
           
_*注：集群的每一台机器都需要执行以上操作以保证能够互相免密登录_

[a](/IV.HDP权限控制与安全保障/安装KDC服务器.md)