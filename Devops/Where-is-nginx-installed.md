I want to know where nginx is installed.
```shell
which nginx
```
Nothing comes out.

But I have passenger installed, so I try this.
```shell
which passenger
```

Now I know where passenger is.
```
/home/deploy/.rvm/gems/ruby-2.1.4@danche/bin/passenger
```

Then I use the passenger command line tool to find nginx.
```shell
/home/deploy/.rvm/gems/ruby-2.1.4@danche/bin/passenger-memory-stats
```

And here comes the nginx.
```
Version: 4.0.53
Date   : 2017-06-14 10:51:15 +0800
------------- Apache processes -------------
*** WARNING: The Apache executable cannot be found.
Please set the APXS2 environment variable to your 'apxs2' executable's filename, or set the HTTPD environment variable to your 'httpd' or 'apache2' executable's filename.


--------- Nginx processes ---------
PID   PPID  VMSize   Private  Name
-----------------------------------
1306  1     39.4 MB  ?        nginx: master process /usr/local/nginx/sbin/nginx
```

Reference: [Installing Passenger + Nginx on a Linux/Unix production server](https://www.phusionpassenger.com/library/walkthroughs/deploy/ruby/ownserver/nginx/oss/trusty/install_passenger.html)