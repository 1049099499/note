# 编译redis
``` shell
wget https://download.redis.io/releases/redis-5.0.12.tar.gz
tar -xzvf redis-5.0.12.tar.gz
cd src
make
```

# 配置redis
```ini
#端口
port 6379
#绑定的IP，多机部署的时候，注意配置该地址，如果是127.0.0.1将会连不上，需要配置为内网地址
bind 127.0.0.1
#数据存放的目录，注意启动服务前，先创建好该目录
dir /usr/local/redis/data
#后台运行,默认为no，使用配置文件方式运行该项要配置为yes
daemonize yes
#开启集群
cluster-enabled yes
#集群的配置文件
cluster-config-file node7001.conf
#AOF方式追加刷盘
appendonly yes
#外网是否可以访问，默认是yes,如果配置了yes,只有在bind中指定的IP可以访问
protected-mode no
#当前节点的密码
requirepass redis
#主节点的密码
masterauth redis
#日志，默认是不开启日志
logfile /usr/local/redis/logs.log
```
# 启动redis-server
``` shell
redis-server /etc/redis/redis.conf
```
