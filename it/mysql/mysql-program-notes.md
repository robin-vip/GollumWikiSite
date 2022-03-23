# mysql program notes

1. **获取数据库和表结构信息**
```mysql
SELECT * FROM information_schema.`TABLES` where TABLE_SCHEMA = '数据库名';
SELECT * FROM information_schema.`COLUMNS` where TABLE_SCHEMA = '数据库名' and TABLE_NAME = '数据表名';
```

2. 创建一个表，和原来表的结构一致
```mysql
CREATE TABLE 新表 LIKE 旧表;
```

3. 获取记录数
```mysql
SELECT count(*) FROM db_name.table_name e;
```

4. 获取指定范围的记录
```mysql
SELECT * FROM db_name.table_name e limit 500,100;  （第500行到1500行 (从0开始计数)）
```

5. 删除某表的所有数据
```mysql
DELETE FROM db_name.table_name;
```
