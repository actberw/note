### shell常用命令使用
1. netcat

     $ nc -l 1234 > sd #接受者
     $ nc 192.168.1.97 1234 < ./feeds.py.back #发送者

2. ngrep 

    $ ngrep -q -W byline 'search' host www.google.com.hk and port 80

3. 查看进程启动时间

    $ ps -p pid -o lstart
4. diff
[http://blog.jobbole.com/26251/](http://blog.jobbole.com/26251/)
