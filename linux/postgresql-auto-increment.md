### postgresql auto increment id

1 . Serial Types

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
