###禁用SELinux和PackageKit

1.  编辑/etc/selinux/config
        
        vim /etc/selinux/config

        #确认SELINUX为禁用状态
        SELINUX=disabled
        
        
             
2. 编辑 /etc/yum/pluginconf.d/refresh-packagekit.conf



