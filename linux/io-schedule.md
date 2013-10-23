#### linux io调度策略
四种算法:
1. cfq (completely fair queueing) (elevator=cfg)  
2. Deadline (elevator=deadline)
3. NOOP (elevator=noop)
4. Anticipatory (elevator=as)

5. 查看 linux中IO调度方法:
    
    $ cat /sys/block/{DEVICE-NAME}/queue/scheduler

1. http://www.php-oa.com/2010/01/03/linux-io-elevator.html
2. http://www.oschina.net/question/565065_77220
3. http://blog.hesey.net/2012/10/linux-io-scheduler-extended.html
4. http://blog.chinaunix.net/uid-26860961-id-3164937.html
5. http://blog.csdn.net/unbutun/article/details/5889208
