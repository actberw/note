### 查看系统安装的时间
1. bin, daemon, sys, adm 等这些帐号的建立时间

    $ passwd -S bin

2. 查看 lost+found 目录状态，因为这个目录一般很少用到

    $ stat /lost+found/
