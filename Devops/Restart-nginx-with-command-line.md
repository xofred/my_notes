Here’s how to send the QUIT (Graceful Shutdown) signal to the NGINX master process:
```shell
kill -QUIT $( cat /usr/local/nginx/logs/nginx.pid )
```

Basic Example of Starting NGINX
```shell
/usr/bin/nginx
```

Advanced Example of Starting NGINX
```shell
/usr/bin/nginx -t -c ~/mynginx.conf -g "pid /var/run/nginx.pid; worker_processes 2;"
```

Reference: [Starting, Stopping, and Restarting NGINX](https://www.nginx.com/resources/wiki/start/topics/tutorials/commandline/)