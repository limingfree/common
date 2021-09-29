# ZooKeeper

# 1. 安装

```shell
wget https://mirrors.tuna.tsinghua.edu.cn/apache/zookeeper/zookeeper-3.6.1/apache-zookeeper-3.6.1-bin.tar.gz
tar -xf apache-zookeeper-3.6.1-bin.tar.gz
cd apache-zookeeper-3.6.1-bin
cp ./conf/zoo_sample.cfg ./conf/zoo.cfg
./bin/zkServer.sh start
```

​	参考：https://www.cnblogs.com/expiator/p/9853378.html	https://blog.csdn.net/java_66666/article/details/81015302

# 2.客户端启动

```shell
./zkCli.sh -server localhost:8181
```

