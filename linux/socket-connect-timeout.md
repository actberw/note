过程如下：
(1)调用fcntl，将socket置为非阻塞模式; 
(2)connect(); 
(3)判断connect()的返回值,一般情况会返回-1,这时你还必须判断错误码如果是EINPROGRESS,那说明connect还在继续;如果错误码不是前者那么就是有问题了,不必往下执行,必须关掉socket;待下次重联; 
(4)select();设置好函数中的超时时间,将select()中的read和write置位,在超时时间内,如果select返回1,即描述字变为了可写,那么连接成功。 如果返回2,即描述字变为即可读又可写,那么出错。 如果返回0,那么超时