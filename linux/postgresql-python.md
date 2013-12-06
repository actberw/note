###python连接postgresql
1. 安装依赖

        sudo aptitude install libpq-dev
        sudo pip install psycopg2
2. 使用

        import psycopg2
        # 创建连接
        conn = psycopg2.connect(host=host, port=port, user=user, password=password, database=db)
        # 创建 cursor
        cursor = conn.cursor()
        cursor.execute("select max(id) from test;") # 如果是update操作需要调用cursor.connection.commit()
        max_id, = cursor.fetchone()
        # 默认对于char, varchar, text类型,返回得是str，需要返回unicode 
        psycopg2.extensions.register_type(psycopg2.extensions.UNICODE) # return unicode
        psycopg2.extensions.register_type(psycopg2.extensions.UNICODEARRAY)

