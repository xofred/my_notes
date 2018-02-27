```conf
# /etc/logrotate.conf

# specify log file(s) location
/data/deploy/elephant_server/current/log/*.log {
  size 100M # rotate immediately when larger than this
  rotate 5 # how many rotate should be keep, combined with size here we only keep 500M log
  dateext # add date format as -%Y%m%d to the end of filename，default is filename.number
  missingok
  nocompress # default new rotate is compressed
  copytruncate # keep writing log to new rotate
}
```

More usages can reference `man logrotate`

Reference: 

[Rotating Rails Production Logs with LogRotate](https://gorails.com/guides/rotating-rails-production-logs-with-logrotate)

[HowTo: The Ultimate Logrotate Command Tutorial with 10 Examples](https://www.thegeekstuff.com/2010/07/logrotate-examples/)

[Centos/Linux setting logrotate to maximum file size for all logs](https://stackoverflow.com/questions/20162176/centos-linux-setting-logrotate-to-maximum-file-size-for-all-logs)