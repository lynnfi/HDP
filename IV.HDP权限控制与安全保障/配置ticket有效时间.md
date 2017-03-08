###设置ticket有效时间

1. 定义申请认证的主机的票据和重新认证生命周期


```
/etc/krb5.conf
 ticket_lifetime = 1d
 renew_lifetime = 12d
```


2 在KDC中定义票据的票据和更新认证生命周期


```
kadmin.local:  getprinc search/ansible-master
Principal: search/ansible-master@for_hadoop
Expiration date: [never]
Last password change: Tue Jun 04 17:58:38 PDT 2013
Password expiration date: [none]
Maximum ticket life: 1 day 01:00:00
Maximum renewable life: 0 days 00:00:00
修改时间的方法：modprinc -maxrenewlife 7days -maxrenewlife 12d  search/ansible-master
```

