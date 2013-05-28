### 在debian 7上安装postgresql 9.2    
默认debian 7 中带的是9.1版本, 9.2带来的主要新特性:  
1. Index-only scans  
2. Replication improvements  
3. JSON datatype  
4. Range Types  

安装方法:  

    $ sudo echo "deb http://apt.postgresql.org/pub/repos/apt/ wheezy-pgdg main" > /etc/apt/sources.list.d/wheezy-pgdg.list  # 增加源  
    $ wget --quiet -O - http://apt.postgresql.org/pub/repos/apt/ACCC4CF8.asc | sudo apt-key add -  # Import the repository key  
    $ sudo apt-get update

这时默认的postgresql就是9.2了, 直接`aptitude install postgresql` .
