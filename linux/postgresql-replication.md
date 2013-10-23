http://www.cnblogs.com/mchina/archive/2012/05/26/2518350.html
2.  `alter role buzz Replication;`增加repication 权限
3. http://www.palominodb.com/blog/2012/08/01/cascade-replication-and-delayed-servers-postgresql-92
4. pg_basebackup -D ./ -F p -v -h 192.168.1.112 -U buzz -W
5. pg_basebackup -D ./ -F t -z -v  -h 192.168.1.112 -U buzz -W
6. http://www.cnblogs.com/mchina/archive/2013/04/19/3028573.html
7. http://blogs.xn--7et027a6ih.xn--fiqs8s/articles/2013/06/19/1371650947083.html
8. 查看复制状态 `select * from pg_stat_replication;`
