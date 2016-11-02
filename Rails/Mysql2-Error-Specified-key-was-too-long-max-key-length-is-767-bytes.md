At the last steps of cap deploy, I met this error when executing `rake db:migrate`
```shell
Mysql2::Error: Specified key was too long; max key length is 767 bytes
```

So I checked the db on server

```sql
SELECT * FROM information_schema.SCHEMATA;
```

```shell
+--------------+-----------------------+----------------------------+------------------------+----------+
| CATALOG_NAME | SCHEMA_NAME           | DEFAULT_CHARACTER_SET_NAME | DEFAULT_COLLATION_NAME | SQL_PATH |
+--------------+-----------------------+----------------------------+------------------------+----------+
| def          | information_schema    | utf8                       | utf8_general_ci        | NULL     |
| def          | test                  | utf8mb4                    | utf8mb4_unicode_ci     | NULL     |
+--------------+-----------------------+----------------------------+------------------------+----------+
```

Turn out to be I accidentally create the db with charset utf8mb4. 

```sql
SHOW CHAR SET WHERE Charset LIKE "%utf8%";
```

```shell
+---------+---------------+--------------------+--------+
| Charset | Description   | Default collation  | Maxlen |
+---------+---------------+--------------------+--------+
| utf8    | UTF-8 Unicode | utf8_general_ci    |      3 |
| utf8mb4 | UTF-8 Unicode | utf8mb4_general_ci |      4 |
+---------+---------------+--------------------+--------+
2 rows in set (0.00 sec)
```

For innodb( such as mysql2), utf8 Maxlen is 3, so the max chars is `767 / 3 = 255`, which is ok by rails default. But utf8mb4 has only `767 / 4 = 191` chars, which will raise error like that.

To fix this, I recreate the db with utf8

```sql
CREATE DATABASE mydatabase CHARACTER SET utf8 COLLATE utf8_general_ci;
```

Reference:

[How do I see what character set a MySQL database / table / column is?](http://stackoverflow.com/questions/1049728/how-do-i-see-what-character-set-a-mysql-database-table-column-is)

[how to create database with charset utf-8](http://dba.stackexchange.com/questions/76788/how-to-create-database-with-charset-utf-8/76789)

[阿里云 Rails 项目调整 RDS MySQL 编码为 utf8mb4 的详细步骤](https://ruby-china.org/topics/24693)