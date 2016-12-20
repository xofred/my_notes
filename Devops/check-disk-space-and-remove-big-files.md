### df -- display free disk space

`df -Th`

-T display partition type

-h human readable

```
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/vda1      ext4       20G   16G  3.3G  83% /
udev           devtmpfs  5.9G  4.0K  5.9G   1% /dev
tmpfs          tmpfs     1.2G  284K  1.2G   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     5.9G     0  5.9G   0% /run/shm
/dev/vdb       ext4      200G   59G  132G  31% /data
```

### du -- display disk usage statistics

`du -sh *`

-s calculate first level sub folder size (aka -d 0)

-h human readable

```
20G	deploy
897M	elasticSearch
2.3M	logs
16K	lost+found
```

### ls -- list directory contents

`ls -rlhS` or `ls -rlht`

-r reverse order (by size -S or modified time -t)

-l list format, with total size at the begining

-h human readable

-S sort by size

-t sort by modified time

```
total 75376
-rw-r--r--  1 MD212  staff    14K Nov  4 17:19 staging.log
-rw-r--r--  1 MD212  staff   2.3M Nov 30 11:10 test.log
-rw-r--r--  1 MD212  staff    34M Dec  8 11:25 development.log
```