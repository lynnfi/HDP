### 禁用SELinux和PackageKit

1. 禁用selinux
  - 在当前终端禁用SELinux

    `setenforce 0`

  - 永久禁用SELinux
* 
   ```
   vim /etc/selinux/config

   #确认SELINUX为禁用状态
   SELINUX=disabled
   ```

2. 禁用PackageKit

  * 通常在centos和redhat中为开启
  
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


