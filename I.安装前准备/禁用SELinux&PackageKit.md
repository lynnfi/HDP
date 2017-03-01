### 禁用SELinux和PackageKit

1. 编辑/etc/selinux/config

   ```
   vim /etc/selinux/config

   #确认SELINUX为禁用状态
   SELINUX=disabled
   ```

1. 编辑 /etc/yum/pluginconf.d/refresh-packagekit.conf

  ```
  vim /etc/yum/pluginconf.d/refresh-packagekit.conf
  #确认packagekit为禁用状态

   enabled=0
  ```





