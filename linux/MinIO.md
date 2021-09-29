# MinIO(对象存储服务器)

# 安装

```shell
wget https://dl.min.io/server/minio/release/linux-amd64/minio
chmod +x minio
./minio server /data
```

参考：https://docs.minio.io/docs/minio-quickstart-guide.html



# 后台启动

```shell
nohup /app/minio/minio server  --address 0.0.0.0:7002 /minio_data > /app/minio/minio.log 2>&1 &
```



# 使用

```
http://223.84.147.3:7002/minio			minioadmin:minioadmin
```



# 设置永久下载链接

原因是因为minIO没有配置bucket策略，默认情况下，minIO没有配置匿名读写的权限

在bucket菜单栏中点击Edit policy，新增Read权限，（Read Only 或 Read and Write均可），即可通过链接的方式直接访问该文件

参考：https://blog.csdn.net/iKaChu/article/details/105809957



# Windows版本

```
https://dl.min.io/server/minio/release/windows-amd64/minio.exe
minio.exe server D:\

set MINIO_ROOT_USER=admin
set MINIO_ROOT_PASSWORD=password
```

