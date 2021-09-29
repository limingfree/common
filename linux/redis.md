# Redis

# 1. 安装

```shell
#！升级gcc到9以上
yum -y install centos-release-scl
yum -y install devtoolset-9-gcc devtoolset-9-gcc-c++ devtoolset-9-binutils

#！临时将此时的gcc版本改为9
scl enable devtoolset-9 bash
#！或永久改变
echo "source /opt/rh/devtoolset-9/enable" >>/etc/profile

#！下载 redis
wget http://download.redis.io/releases/redis-6.0.6.tar.gz
tar -xf redis-6.0.6.tar.gz
make && make install
```

# 2. 集群安装

```shell
mkdir cluster
mkdir cluster/8000 cluster/8001 cluster/8002
cp redis.conf cluster/8000
cp redis.conf cluster/8001
cp redis.conf cluster/8002
```

```
#! 修改配置文件 cluster/8000/redis.conf, cluster/8001/redis.conf cluster/8002/redis.conf
port 8000 # 客户端连接端口
bind 0.0.0.0 #实例绑定的IP地址
dir /app/redis-6.0.6/cluster/8000 # redis实例数据配置存储位置
daemonize yes # 是否以后台进程的方式启动redis实例
pidfile /var/run/redis_8000.pid # 指定该进程pidfile
cluster-enabled yes # 开启集群模式
appendonly yes # 开启aop日志
protected-mode no # 关闭保护模式
cluster-announce-ip 101.132.163.1 #公网IP
```

```shell
#！启动 redis
redis-server /app/redis-6.0.6/cluster/8000/redis.conf
redis-server /app/redis-6.0.6/cluster/8001/redis.conf
redis-server /app/redis-6.0.6/cluster/8002/redis.conf

#！创建集群
redis-cli --cluster create 101.132.163.1:8000 101.132.163.1:8001 101.132.163.1:8002 
#！ redis-cli --cluster create --cluster-replicas 1 101.132.163.1:8000 101.132.163.1:8001 101.132.163.1:8002 106.15.185.243:9000 106.15.185.243:9001 106.15.185.243:9002
#！ redis-cli --cluster create --cluster-replicas 1 223.84.147.3:8000 223.84.147.3:8001 223.84.147.3:8002 223.84.147.3:9000 223.84.147.3:9001 223.84.147.3:9002
```

# 3. 操作命令

```shell
redis-cli -h 101.132.163.1 -p 8000
101.132.163.1:8000>config set stop-writes-on-bgsave-error no
101.132.163.1:8000>keys *
101.132.163.1:8000>set aa 123
101.132.163.1:8000>get aa
101.132.163.1:8000>del key
101.132.163.1:8000>flushdb
```

# Redis 集群

​	参考：https://blog.csdn.net/qq_42815754/article/details/82912130
​				https://www.cnblogs.com/cjsblog/p/9048545.html
​				https://www.cnblogs.com/paul8339/p/11987345.html
​				https://www.v2ex.com/amp/t/561346



# 4. 监测

```
java -jar redis-stat-0.4.14.jar host/password --server=7100
```

