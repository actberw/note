### shell常用命令使用
1. netcat

     $ nc -l 1234 > sd #接受者
     $ nc 192.168.1.97 1234 < ./feeds.py.back #发送者

2. ngrep 

    $ ngrep -q -W byline 'search' host www.google.com.hk and port 80
