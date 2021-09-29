

# SVN

# 1.安装

```shell
yum install subversion
```

# 2.配置

```shell
mkdir /svn_root/software/smartcity2 -p
svnadmin create /svn_root/software/smartcity2
cd /svn_root/software/smartcity2/conf
```

```properties
vi passwd

[users]
li = li123
tian = tian123
tan = tan123
```

```properties
vi authz

[/]
li = rw
tian = rw
tan = rw
* = 
```

```properties
vi svnserve.conf

anon-access = read
auth-access = write
password-db = passwd
realm = /svn_root/software/smartcity2
```

# 3.启动服务

```shell
svnserve -d -r /svn_root --listen-port 7690 --log-file /svn_root/svnserve.log
```

# 4.客户端连接

1.  windows资源管理器右键  TortoiseSVN ->  Repo-browser
2.  URL输入       svn://223.84.147.58:7690/software/smartcity2

# 5.登录

​	用户名为姓氏全拼；密码为姓氏全拼+123