# Kafka

## 1. 安装

```shell
wget https://mirror.bit.edu.cn/apache/kafka/2.6.0/kafka_2.13-2.6.0.tgz
tar -zxf kafka_2.13-2.6.0.tgz
cd kafka_2.13-2.6.0
# 须先启动 zookeeper
./bin/kafka-server-start.sh ./config/server.properties &
nohup bin/kafka-server-start.sh config/server.properties >/dev/null 2>&1 &

# 配置 
vi config/server.properties
		listeners=PLAINTEXT://172.16.2.75:8092
		advertised.listeners=PLAINTEXT://223.84.147.58:8092
```

​	参考：https://www.cnblogs.com/expiator/p/9990171.html	https://blog.csdn.net/weixin_39984161/article/details/91971731

## 2. 使用

```
./bin/kafka-topics.sh --create --zookeeper localhost:8181 --replication-factor 1 --partitions 1 --topic tp_test
./bin/kafka-topics.sh -list -zookeeper localhost:8181
./bin/kafka-topics.sh -zookeeper localhost:8181 -describe -topic iot_data
./bin/kafka-console-producer.sh --broker-list localhost:8092 --topic tp_test
./bin/kafka-console-consumer.sh --bootstrap-server localhost:8092 --topic tp_test --from-beginning
```

