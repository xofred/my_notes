Recently, our production server complained about innodb lock wait time exceeded occasionolly.

```
 Mysql2::Error: Lock wait timeout exceeded; try restarting transaction: UPDATE `shows` SET `poster` = '4d403088c76a3ed89125f4210f003777.jpg', `updated_at` = '2016-12-19 03:12:51.225764' WHERE `shows`.`id` = 144400, show_id: 144400
```

It comes from this code.

```ruby
show.update!(poster: File.open(output_image_path)) # carrierwave 'upload' a loacal file
```

Maybe sometimes it takes too long to finish? So I check the lock wait timeout of our db.

```shell
cat /etc/my.cnf | grep timeout

innodb_lock_wait_timeout = 120
```

Since the poster is not 100% needed for our show. And I want this annoying error gone!

```ruby
require 'timeout'

Timeout::timeout(119) do
  show.update!(poster: File.open(output_image_path)) # carrierwave 'upload' a loacal file
end
```

Reference: 

[innodb_lock_wait_timeout参数的了解](http://blog.itpub.net/12679300/viewspace-1418320/)

[InnoDB：Lock & Transaction](http://www.cnblogs.com/f1194361820/p/6197262.html?utm_source=gold_browser_extension)