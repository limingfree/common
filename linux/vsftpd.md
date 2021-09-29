# vsftpd(ftp服务器)

参考：https://blog.csdn.net/qq_36938617/article/details/89077845

```shell
yum -y install vsftpd
mkdir /ftp_root
useradd ftpuser -d /ftp_root/ -s /sbin/nologin
chown -R ftpuser.ftpuser /ftp_root/
passwd ftpuser ftpuser

vi /etc/vsftpd/vsftpd.conf
local_root=/ftp_root
listen_port=7921
pasv_min_port=7922
pasv_max_port=7999

sudo service vsftpd start
sudo service vsftpd stop
sudo service vsftpd restart
```

