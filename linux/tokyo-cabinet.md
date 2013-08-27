### tokyo tyrant安装
1. 安装tokyo cabinet   

     $ sudo aptitude install libbz2-dev  
     $ wget http://fallabs.com/tokyocabinet/tokyocabinet-1.4.48.tar.gz # downlaod source code  
     $ tar zxvf tokyocabinet-1.4.48.tar.gz; cd tokyocabinet-1.4.48;  
     $ ./configure  
     $ make  
     $ sudo make install  


2. 安装 tokyo tyrant  

    $ wget http://fallabs.com/tokyotyrant/tokyotyrant-1.1.41.tar.gz 
    $ tar zxvf tokyotyrant-1.1.41.tar.gz; cd tokyotyrant-1.1.41/
    $ ./configure
    $ make
    $ sudo make install

3. 启动Tokyo Tyrant服务器端  
  启动参数介绍:  

    - -host name :指明服务器的hostname或者ip地址。默认服务器的所有地址都会被绑定。比如：指定127.0.0.1这样的ip，就只是本地可以访问了。
    - -port num : 指定服务启动的端口. 默认1978.如果要启动多个数据库实例，端口需要不一样。
    - -thnum num : 指定服务工作的线程数。默认8.
    - -tout num : 指定每个会话的超时时间。默认永不超时。
    - -dmn : 以守护进程方式运行。
    - -pid path : 输出进程IP到指定的文件。
    - -log path : 输出日志信息到指定文件。
    - -ld : 日志中记录debug信息。
    - -le :日志中只记录错误信息。
    - -ulog path : 指定存放更新日志（update log）的目录.可以用来备份恢复数据库，主从库之间的同步。
    - -ulim num : 指定每个更新日志文件的大小限制.
    - -uas :使用异步IO记录更新日志。（使用此项可以减少写入日志的IO开销，但是在服务器意外关机，进程被kill时可能会丢失数据。根据经验，一般可以不使用）。
    - -sid num : 指定服务的ID号。主从复制的时候通过不同的ID号来识别。
    - -mhost name : 指定主从复制模式下的主服务器的IP或域名。
    - -mport num : 指定主从模式下主服务器的端口号.
    - -rts path : 指定用于主从复制的时间戳存放文件.
    - -ext path : 指定扩展脚本语言文件。
    - -extpc name period : 指定被周期调用的函数名和间隔时间.
    - -mask expr : 指定被禁止的命令名（比如可以禁止使用清空vanish）.
    - -unmask expr : 指定被允许的命令名.
    - -mul num : 指定多个数据库机制的分区数目。



    $ ttserver -host 192.168.1.97 -port 11211 -thnum 8 -dmn -pid ./ttserver.pid -log ./ttserver.log -le -ulog ./ -ulim 128m -sid 1 -rts ./ttserver.rts  buzz_master.tch 

4. 数据库类型  
 - 如果数据库名为"*"，表示内存hash数据库。
 - 如果数据库名为"+"表示内存tree数据库。
 - 如果数据库名为".tch",则数据库为hash数据库。
 - 如果数据库名的后缀为".tcb"，数据库将为B+ tree数据库。
 - 如果数据库名的后缀为".tcf"。则数据库将为fixed-length数据库。
 - 如果数据库名的后缀为".tct",则数据将为一个table数据库（有表的概念）。

5. 优化  
 - Tokyo Cabinet 单个数据库文件记录数超过1亿，性能会急剧下降。Tokyo Tyrant 的新版本支持了数据库文件拆分，例如 ttserver -mul 256 database.tcb 启动TT时，将会自动拆分成256个文件，存取时，根据key哈希到不同的文件
 - 如果使用hash数据库我们可以指定#bnum=xxx(bucket数量)， #xmsiz=xxx(最大内存使用)来提高性能


Refer:  
 - [http://www.cnblogs.com/sunli/archive/2009/03/08/1406178.html](http://www.cnblogs.com/sunli/archive/2009/03/08/1406178.html)  
 - [http://blog.nosqlfan.com/html/2856.html](http://blog.nosqlfan.com/html/2856.html)
