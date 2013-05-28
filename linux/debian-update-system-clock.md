### 更新debian 系统时间
1. ntp(Network Time Protocol)更新 

    $ sudo aptitude install ntpdate  
    $ sudo ntpdate pool.ntp.org  
    也可以自己建立ntp服务器 `aptitude install ntpd`   
2. 利用date命令

    $ date -s "20120505"  # Sat May  5 00:00:00 CST 2012     
    $ hwclock --systohc  
