`top`
```
  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 1457 deploy    20   0  777484 320640   4948 S   0.0  3.9   0:11.53 ruby
 2856 deploy    20   0  777532 317848   5080 S   0.0  3.9   0:09.81 ruby
 2661 deploy    20   0 1094480  44976   2108 S   0.0  0.6   0:00.10 ruby
 2655 deploy    20   0  213592  43860   1780 S   0.0  0.5   0:00.04 ruby
 2658 deploy    20   0 1094480  43304    972 S   0.0  0.5   0:00.07 ruby
 1308 deploy    20   0   67644  29412   1192 S   0.0  0.4   0:00.09 nginx
```

Press `c`
```
  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 1457 deploy    20   0  777484 320640   4948 S   0.0  3.9   0:11.53 Passenger RackApp: /data/deploy/bike-ticket/current
 2856 deploy    20   0  777532 317852   5084 S   0.0  3.9   0:10.68 Passenger RackApp: /data/deploy/bike-ticket/current
 2661 deploy    20   0 1094480  44976   2108 S   0.0  0.6   0:00.10 puma: cluster worker 1: 2655 [20170614023414]
 2655 deploy    20   0  213592  43872   1788 S   0.0  0.5   0:00.04 puma 3.4.0 (unix:///data/deploy/bike-open-api/shared/tmp/sockets/puma.sock) [20170614023414]
 2658 deploy    20   0 1094480  43304    972 S   0.0  0.5   0:00.07 puma: cluster worker 0: 2655 [20170614023414]
 1308 deploy    20   0   67644  29412   1192 S   0.0  0.4   0:00.10 nginx: worker process
```

Reference: [Show full process name in top](https://serverfault.com/questions/139632/show-full-process-name-in-top)