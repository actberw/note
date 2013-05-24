### ld xxx.so not found
今天安装scribe时提示libthriftz-0.9.0.so 没有找到, 但是明明是刚刚安装的, 在/usr/local/lib/libthriftz-0.9.0.so, 就是ld没有找到，ldd结果如下
>   libthrift-0.9.0.so => not found    
    libthriftnb-0.9.0.so => not found

看了下ld的配置/usr/local/lib, 已经在/etc/ld.so.conf.d/libc.conf, 查了下stackoverflow是ldcache造成的[http://stackoverflow.com/questions/12234010/gcc-linked-libraries-in-usr-local-lib-are-not-found-but-etc-ld-so-conf-d-lib](http://stackoverflow.com/questions/12234010/gcc-linked-libraries-in-usr-local-lib-are-not-found-but-etc-ld-so-conf-d-lib)，ldconfig -p没有libthriftz-0.9.0.so ,执行下ldconfig就好了
