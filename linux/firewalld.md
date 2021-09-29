# firewalld(防火墙)

参考：https://blog.csdn.net/s_p_j/article/details/80979450

```shell
systemctl start firewalld
systemctl stop firewalld

firewall-cmd --list-services 
firewall-cmd --get-services 
firewall-cmd --add-service=<service> 
firewall-cmd --delete-service=<service>

firewall-cmd --zone=public --list-ports
firewall-cmd --zone=public --add-port=8011/tcp --permanent
firewall-cmd --zone=public --remove-port=8080/tcp --permanent

firewall-cmd --reload
```

