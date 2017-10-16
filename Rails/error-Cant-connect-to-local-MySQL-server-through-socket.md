Find out where is mysql.sock located
```shell
sudo find / -type s
```
Then modify socket location in `database.yml`
```ymal
default: &default
  adapter: mysql2
  encoding: utf8
  pool: 5
  username: root
  password: 
  socket: /private/tmp/mysql.sock
```

[error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'](https://stackoverflow.com/questions/11990708/error-cant-connect-to-local-mysql-server-through-socket-var-run-mysqld-mysq)