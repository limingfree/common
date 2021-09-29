# RabbitMQ

```shell
wget https://dl.bintray.com/rabbitmq-erlang/rpm/erlang/22/el/7/x86_64/erlang-22.3.4.4-1.el7.x86_64.rpm
sudo rpm -Uvh erlang-22.3.4.4-1.el7.x86_64.rpm
sudo yum install -y socat
wget https://github.com/rabbitmq/rabbitmq-server/releases/download/v3.8.5/rabbitmq-server-3.8.5-1.el7.noarch.rpm
sudo yum install rabbitmq-server

sudo systemctl start rabbitmq-server
sudo systemctl stop rabbitmq-server

rabbitmq-plugins enable rabbitmq_management
rabbitmqctl add_user admin admin
rabbitmqctl set_user_tags admin administrator
rabbitmqctl set_permissions -p / admin ".*" ".*" ".*"

sudo firewall-cmd --zone=public --add-port=4369/tcp --permanent
sudo firewall-cmd --zone=public --add-port=5672/tcp --permanent
sudo firewall-cmd --zone=public --add-port=15672/tcp --permanent

sudo firewall-cmd --reload
```

