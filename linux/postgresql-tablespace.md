### postgresql 表空间

1. 9.2版本pg_tablespace没有spclocation字段了, 提供了 pg_tablespace_location()函数

     select pg_tablespace_location(16388);

2. 或者执行`\db;`

