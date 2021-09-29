# git

# 服务端

```shell
yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel perl-devel
yum install git

groupadd git
useradd git -g git

cd /home/git/
mkdir .ssh
chmod 755 .ssh
touch .ssh/authorized_keys
chmod 644 .ssh/authorized_keys

cd /home
mkdir gitrepo
chown git:git gitrepo/
cd gitrepo

git init --bare smartcity.git
chown -R git:git smartcity.git
```



# 客户端

```shell
ssh-keygen –t rsa –C “18618286421@126.com”
将C:\Users\Administrator\.ssh\id_rsa.pub中的内容，拷贝至【服务端】中的/home/git/.ssh/authorized_keys。 一个用户一行

git clone ssh://git@223.84.147.58:30022/home/gitrepo/smartcity.git
```



## 常用操作

```shell
git add .
git commit -m "first commit"
git push

git pull
```



参考： https://www.runoob.com/git/git-server.html   https://blog.csdn.net/qq_38798859/article/details/90753052



```sh
echo "# linux" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/limingfree/linux.git
git push -u origin main
```

```sh
git remote add origin https://github.com/limingfree/linux.git
git branch -M main
git push -u origin main
```

