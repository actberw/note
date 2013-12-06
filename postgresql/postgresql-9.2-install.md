### 在debian 7上安装postgresql 9.2    

默认debian 7 中带的是9.1版本, 9.2带来的主要新特性:

- Index-only scans  
- Replication improvements  
- JSON datatype  
- Range Types  


1. 安装方法:

        $ sudo echo "deb http://apt.postgresql.org/pub/repos/apt/ wheezy-pgdg main" > /etc/apt/sources.list.d/wheezy-pgdg.list  # 增加源  
        $ wget --quiet -O - http://apt.postgresql.org/pub/repos/apt/ACCC4CF8.asc | sudo apt-key add -  # Import the repository key  
        $ sudo apt-get update

   这时默认的postgresql就是9.2了, 直接`aptitude install postgresql` .

2. 配置权限
postgresl通过pg_hba.conf 文件控制连接权限, 共五列.
 - type: host or local, local是通过Unix domain socket connection
 - METHOD: "trust", "reject", "md5", "password", "gss", "sspi", "krb5", "ident", "peer", "pam", "ldap", "radius" or "cert". 常用得是md5,


        # 示例配置 
        # TYPE  DATABASE        USER            ADDRESS                 METHOD
        host    all             all             127.0.0.1/32            md5
        host    all             all             192.168.1.0/24          md5
