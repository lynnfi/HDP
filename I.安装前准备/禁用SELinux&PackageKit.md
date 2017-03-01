### 禁用SELinux和PackageKit

1. 编辑/etc/selinux/config

   ```
   vim /etc/selinux/config

   #确认SELINUX为禁用状态
   SELINUX=disabled
   ```

2. 编辑 /etc/yum/pluginconf.d/refresh-packagekit.conf

  ```
  vim /etc/yum/pluginconf.d/refresh-packagekit.conf

   #确认packagekit为禁用状态
   enabled=0
  ```

3. 检查UMASK 

  - 检查系统UMASK
  
    `umask`

  - 设置当前UMASK
  
    `umask 0022`
    
  - 永久生效
  
    `echo umask 0022 >> /etc/profile`


