## ubuntu下安装scribe

scirbe 依赖于boost, libevent, thrift, fb303(控制scribe节点)
### 1\. 安装依赖 
见另一篇thrift得文章，这里只说下fb303得安装, fb303 在thrift源码包得contrib目录  

     $ cd contrib/fb303
     $ ./configure CPPFLAGS="-DHAVE_INTTYPES_H -DHAVE_NETINET_IN_H"
     $ make
     $ sudo make install
### 2\. 安装scribe

     $ git clone https://github.com/facebook/scribe.git
     $ cd scribe
     $ ./bootstrap.sh CPPFLAGS="-DHAVE_INTTYPES_H -DHAVE_NETINET_IN_H -DBOOST_FILESYSTEM_VERSION=2" # -DBOOST_FILESYSTEM_VERSION=2 参数只有在你的boost版本大于1.46的时候需要添加
     $ make 
     $ sudo make install
### 3\. 测试

     $ cd examples
     $ scribed -c examples/example1.conf
     $ mkdir scribetest
     $ echo  "hello world"|./scribe_cat test
     $ cat /tmp/scribetest/test/test_current
显示hello world 即正常。  

### 4\.安装遇到得问题  
1\. 编译fb303的时候: "error: ‘uint32_t’ does not name a type"  

./configure 需要加参数 CPPFLAGS="-DHAVE_INTTYPES_H -DHAVE_NETINET_IN_H"

2\. 链接又报/usr/bin/ld: cannot find -lthriftnb,  没有安装 libevent-dev

3\. undefined reference to boost::system::generic_category(), 两种解决办法:  

1. 找到出错得g++那一行, 进入到src目录, 把 `-lboost_system-mt -lboost_filesystem-mt` 参数放到最后.  
2. configure加参数 在configure的时候加上`-lboost_system-mt -lboost_filesystem-mt`参数

4\. 执行测试得时候提示 "ImportError: No module named scribe" , 因为默认python包是安装在site-packages，site-packages不再搜索目录中

     cp -a /usr/lib/python2.7/site-packages/* /usr/lib/python2.7/dist-packages/
   即可。

5\. 启动scribe时提示" error while loading shared libraries: libthrift-0.9.0.so", 应该是/usr/local/lib/不在ld得搜索目录中  
    
     $ ldd `which scribed`  
     libthriftnb-0.9.0.so => not found   
     $ echo "export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib" >> ~/.bashrc
     $ source ~/.bashrc
6\. thrift No output language(s) specified, 编辑src/Makefile thrift命令这一行，把参数-cpp 变成-gen cpp

#### 参考链接:

1. http://note2share.com/post/32b5f6a7-f069-44a4-9b7f-920c14cb42e5
2. http://www.nosql.se/2012/10/tutorial-installing-scribe-on-debianubuntu/
3. http://my.oschina.net/guol/blog/110236

