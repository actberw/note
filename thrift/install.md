## 在ubuntu上安装thrift(0.9.0)

### 1\. 包依赖  
详细信息见[http://thrift.apache.org/docs/install/](http://thrift.apache.org/docs/install/)  
大致上有g++, autoconf, automake, libtool, pkg-config, libevent, boost, 及相应得dev库

     $ aptitude install autoconf automake libtool pkg-config libtool libevent-dev libevent-2.0-5 libboost-all-dev
### 2\. 下载源代码  

     $ wget http://ftp.kddilabs.jp/infosystems/apache/thrift/0.9.0/thrift-0.9.0.tar.gz

### 3\. 安装
解压缩  

     $ tar zxvf thrift-0.9.0.tar.gz
     $ cd thrift-0.9.0
编译  

     $ ./configure --help #查看帮助信息, --with-libevent， --with-boost用于指定安装位置, --with-python=yes/no类似的可以打开关闭对某些语言得支持，默认全部打开得。
     $ ./configure --with-ruby=no  CPPFLAGS="-DHAVE_INTTYPES_H -DHAVE_NETINET_IN_H"
     $ make
     $ sudo make install

查看是否编译成功

     $ thrift -version
显示: Thrift version 0.9.0, 则安装成功。
