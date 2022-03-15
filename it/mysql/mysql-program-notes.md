# mysql program notes

1. **获取数据库和表结构信息**
```mysql
SELECT * FROM information_schema.`TABLES` where TABLE_SCHEMA = '数据库名';
SELECT * FROM information_schema.`COLUMNS` where TABLE_SCHEMA = '数据库名' and TABLE_NAME = '数据表名';
```