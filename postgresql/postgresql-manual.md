#### postgresql管理中常用得操作
1. 查询活动得链接

        select * from pg_stat_activity;
2. 关闭连接

        select pg_cancel_backend(pid)
        select pg_terminate_backend(19161);

3. truncate table同时set auto increment 从1开始

        truncate table table_name RESTART IDENTITY;

4. 数据库大小

        `select pg_database.datname,pg_size_pretty(pg_database_size(pg_database.datname)) AS size from pg_database;`

5. Serial Types(自增类型)  
    The data types serial and bigserial are not true types, but merely a notational convenience for setting up unique identifier columns (similar to the AUTO_INCREMENT property supported by some other databases). In the current implementation, specifying:

        CREATE TABLE tablename (
            colname SERIAL
        );
is equivalent to specifying:

        CREATE SEQUENCE tablename_colname_seq;
        CREATE TABLE tablename (
            colname integer NOT NULL DEFAULT nextval('tablename_colname_seq')
        );
        ALTER SEQUENCE tablename_colname_seq OWNED BY tablename.colname;

6. 9.2版本pg_tablespace没有spclocation字段了, 提供了 pg_tablespace_location()函数

        select pg_tablespace_location(16388);
        # or 
        \db;
