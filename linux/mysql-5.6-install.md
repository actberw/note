### debian 上安装mysql-5.6.14
1. 下载deb包

        wget http://dev.mysql.com/get/Downloads/MySQL-5.6/mysql-5.6.14-debian6.0-x86_64.deb
2. 安装

        sudo dpkg -i ./mysql-5.6.14-debian6.0-x86_64.deb # 需要安装依赖: libaio-dev
3. 安装默认数据库

        sudo mysql_install_db  --datadir=datadir
4. 配置并启动mysql, 默认msyql安装到*/opt/mysql/server-5.6*目录 

        ln -s /opt/mysql/server-5.6 /usr/lcoal/mysql
        # 修改 PATH
        export PATH=$PATH:/usr/local/mysql/bin
        # init.d脚本
        cd /opt/mysql/server-5.6;sudo cp support-files/mysql.server /etc/init.d/mysql
        # 修改配置文件
        # datadir, bind-address, log, innodb_file_per_table

        # 启动mysql
        sudo /etc/init.d/mysql start

5. 修改root密码，删除测试数据库

        mysql_secure_installation # 可能需要 ln -s /var/run/mysqld/mysqld.sock /tmp/mysql.sock

6. 增加账户,授权

        # add user
        create user 'acc'@'%' identified by "123"
        FLUSH PRIVILEGES;
        # create database        
        create database test_1 DEFAULT CHARACTER SET utf8;
        # grant, revoke 
        grant SELECT,INSERT,UPDATE,DELETE on test_1.* to 'acc'@'%';

遇到得错误提示:  

- Using unique option prefix key_buffer instead of key_buffer_size is deprecated and will be removed in a future release. Please use the full name instead  
  把key_buffer 换成 key_buffer_size

- IMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).
  修改/etc/my.cnf mysqld 增加 explicit_defaults_for_timestamp=1 

- Can't find messagefile '/usr/share/mysql/errmsg.sys
  增加 lc-messages-dir=/usr/local/mysql/share 选项
