# 本地安装nginx和passenger

## =====nginx=====

### brew安装

`brew install nginx`

The default port has been set in /usr/local/etc/nginx/nginx.conf to 8080 so that nginx can run without sudo.

nginx will load all files in /usr/local/etc/nginx/servers/.

### 下载源码包编译（需要第三方模块用这种安装）

1. 下载源码包

2. 解压

3. 切换到解压路径，编译（需要第三方模块这时候加入）

⚠ 如出现找不到第三方模块的报错，将其拷贝至nginx目录

```
./configure --add-module=<path to upload module sources>
make
sudo make install
```

### 运行

To have launchd start nginx at login:

  `ln -sfv /usr/local/opt/nginx/*.plist ~/Library/LaunchAgents`

Then to load nginx now:

  `launchctl load ~/Library/LaunchAgents/homebrew.mxcl.nginx.plist`

Or, if you don't want/need launchctl, you can just run:

  `nginx`

### 终止运行

`/usr/bin/nginx -s stop`

### 测试

访问[http://localhost:8080/](http://localhost:8080/)测试是否运行

## ====passenger====

### 加入项目Gemfile

`gem "passenger"`

bundle install

### rails改用passenger

`bundle exec passenger start`
