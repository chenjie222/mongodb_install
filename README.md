#### 1、下载安装包

```
curl -O https://github.com/chenjie222/mongodb_install/raw/master/package/mongodb-linux-x86_64-4.0.4.tgz
```

#### 2、解压

```
tar -zxvf mongodb-linux-x86_64-4.0.4.tgz
```

#### 3、移动到指定位置

```
mv  mongodb-linux-x86_64-4.0.4/ /opt/mongodb
```

#### 4、在/data/mongodb下创建文件夹

```
mkdir -p /data/mongodb/conf
mkdir -p /data/mongodb/db
mkdir -p /data/mongodb/logs
```

在 /data/mongodb/conf 新建 default.conf

vim default.conf

```
dbpath=/data/mongodb/db
logpath=/data/mongodb/logs/mongodb.log
port=8091
fork=true
bind_ip=0.0.0.0
```

#### 6、环境变量配置

vi /etc/profile 

export MONGODB_HOME=`/opt/mongodb`

export PATH=`$PATH:$MONGODB_HOME/bin`

保存后，重启系统配置

source /etc/profile

#### 7、启动

在 /data/mongodb/conf下

mongod -f default.conf

8、关闭

mongod -f ./default.conf --shutdown  或./mongod -f ./default.conf --shutdown

#### 7、数据同步

```
备份
mongodump -h 10.110.156.60:8091 -d file_mgr_db -o /root/mongodb/
同步
mongorestore -h 192.168.3.39 --port 8091 -d file_mgr_db --dir /root/mongodb/file_mgr_db
```



