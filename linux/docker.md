# docker

详细参考：https://www.runoob.com/docker/centos-docker-install.html

```shell
sudo systemctl start docker
docker pull rabbitmq:latest
docker run -d --name rabbitmq-test -p 5672:5672 -p 15672:15672 -e RABBITMQ_DEFAULT_USER=yckj -e RABBITMQ_DEFAULT_PASS=ycc2020 rabbitmq
docker ps
docker container ls -a
docker container start rabbitmq-test
docker container stop rabbitmq-test
docker container rm rabbitmq-test

docker exec -it rabbitmq-test /bin/bash
rabbitmq-plugins enable rabbitmq_management
docker exec -it redis-test /bin/bash
```

