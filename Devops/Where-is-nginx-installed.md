For getting the list of all running nginx processes, the ps utility may be used, for example, in the following way:
```shell
ps -ax | grep nginx
```
```
 1324 ?        Ss     0:00 nginx: master process /usr/local/nginx/sbin/nginx
 1325 ?        S      0:00 nginx: worker process
 1326 ?        S      0:00 nginx: worker process
 1327 ?        S      0:00 nginx: worker process
 1328 ?        S      0:00 nginx: worker process
 1329 ?        S      0:00 nginx: worker process
 1330 ?        S      0:00 nginx: worker process
 1331 ?        S      0:00 nginx: worker process
 1332 ?        S      0:00 nginx: worker process
 9540 pts/0    S+     0:00 grep --color=auto nginx
```

Reference: [Beginner’s Guide](http://nginx.org/en/docs/beginners_guide.html#control)