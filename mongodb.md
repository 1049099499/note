# mongodb集群部署
## 一主二从
准备三台服务器
- 192.168.88.100
- 192.168.88.101
- 192.168.88.102
## 配置

``` yml
 # mongod.conf

# for documentation of all options, see:
#   http://docs.mongodb.org/manual/reference/configuration-options/

# Where and how to store data.
storage:
  dbPath: /usr/local/mongodb/data/
  journal:
    enabled: true
#  engine:
#  mmapv1:
#  wiredTiger:

# Where and how to log messages.
systemLog:
  destination: file
  logAppend: true
  path: /usr/local/mongodb/log/db.log
  logRotate: reopen

# What type of connections to allow.
net:
  port: 3718
  bindIp: 192.168.88.100,localhost
  ipv6: true


# How to manage mongod.
processManagement:
  fork: true

# Full path to pidfile (if not set, no pidfile is created)
  pidFilePath: /usr/local/mongodb/mongod.pid

setParameter:
  enableLocalhostAuthBypass: 1

# Security settings.
security:
  authorization: enabled
  keyFile: /usr/local/mongodb/.keyfile
  
#operationProfiling:
replication:
  replSetName: dvs-cms
  oplogSizeMB: 10240
```

