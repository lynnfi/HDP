###Python2.7配置

7. 安装sqllit3

       yum install sqlite3-devel -y
        easy_install pysqlite

1. 安装开发库文件
    
        yum install zlib-devel openssl-devel sqlite-devel

2. 下载Python

        wget https://www.python.org/ftp/python/2.7.8/Python-2.7.8.tgz
        tar zxvf Python-2.7.8.tgz
        
3. 编译安装(安装路径:/usr/local)
    ```
    cd Python-2.7.8 
    ./configure --prefix=/usr/local
    make & make install
    ```
    
4. 替代原有python

        mv /usr/bin/python /usr/bin/python2.6 
        ln -sf /usr/local/bin/python2.7 /usr/bin/python
5. 修正yum
        
        vim /usr/bin/yum
        
        将文件开头改为:
        #!/usr/bin/python2.6
6. 安装setuptools和pip

        wget https://bootstrap.pypa.io/get-pip.py
        python get-pip.py
        #建立软连接
        ln -sf /usr/local/bin/pip /usr/bin/pip
        ln -sf /usr/local/bin/easy_install /usr/bin/easy_install

        
安装pip的第二种方案（已经有setuptools的情况下使用）：
        
* 安装epel扩展源：
    
        yum -y install epel-release
    
* 更新完成之后，装pip：
    
       yum -y install python-pip
　　
* 安装完成之后清除cache：
　　
        yum clean all