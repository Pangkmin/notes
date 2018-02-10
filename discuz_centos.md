### 准备 LAMP 环境
LAMP 是 Linux、Apache、MySQL 和 PHP 的缩写，是 Discuz 论坛系统依赖的基础运行环境。我们先来准备 LAMP 环境

#### 安装 MySQL
使用 yum 安装 MySQL：
```base
yum install mysql-server -y
```

若在centos mysql安装时报No package mysql-server available错误是因为我们本地yum仓库中没有可用的mysql-server rpm包，因此在yum安装之前先在本地备好rpm软件包。<br/>
在Centos 7上使用:
```base
[root@VM_230_32_centos ~]# rpm -ivh https://repo.mysql.com//mysql57-community-release-el7-11.noarch.rpm
Retrieving 
https://repo.mysql.com//mysql57-community-release-el7-11.noarch.rpm
warning: /var/tmp/rpm-tmp.7OOdD1: Header V3 DSA/SHA1 Signature, key ID 5072e1f5: NOKEY
Preparing... ################################# [100%]
Updating / installing...
1:mysql57-community-release-el7-11 ################################# [100%]
[root@eb2476e8763c /]#
```
rpm软件包安装好之后，我们就可以使用yum install mysql-server命令来安装mysql了。


安装完成后，启动 MySQL 服务：
```base
service mysqld restart
```
此实验使用 mysql 默认账户名和密码，您也可以设置自己的 MySQL 账户名和密码：[?]，参考下面的内容：
```base
 /usr/bin/mysqladmin -u root password 'rootmysql'
```
若出现：
```base
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
```
获取MySQL的临时密码：
```base
grep 'temporary password' /var/log/mysqld.log
```
用默认密码登录
```base
shell> mysql -uroot -p
mysql> Enter password: Q2>r4=l-DWIP
```
修改默认密码
```base
mysql> SET PASSWORD = PASSWORD('root');
# 上面的root是你的新密码
```

将 MySQL 设置为开机自动启动：
```base
chkconfig mysqld on
```

#### 安装 Apache 组件
使用 yum 安装 Apache 组件：
```base
yum install httpd -y
```
安装之后，启动 httpd 进程：
```base
service httpd start
```
把 httpd 也设置成开机自动启动：
```base
chkconfig httpd on
```
#### 安装 PHP
使用 yum 安装 PHP:
```base
yum install php php-fpm php-mysql -y
```
安装之后，启动 PHP-FPM 进程：
```base
service php-fpm start
```
启动之后，可以使用下面的命令查看 PHP-FPM 进程监听哪个端口
```base
netstat -nlpt | grep php-fpm
```
把 PHP-FPM 也设置成开机自动启动：
```base
chkconfig php-fpm on
```
CentOS 6 默认已经安装了 PHP-FPM 及 PHP-MYSQL，下面命令执行的可能会提示已经安装。
PHP-FPM 默认监听 9000 端口

### 安装并配置 Discuz
#### 安装 Discuz
CentOS 6 没有Discuz 的 yum 源，所以我们需要下载一个Discuz 压缩包：
```base
wget http://download.comsenz.com/DiscuzX/3.2/Discuz_X3.2_SC_UTF8.zip
````
下载完成后，解压这个压缩包:
```base
unzip Discuz_X3.2_SC_UTF8.zip
```
若报错：-bash: unzip: command not found  <br/>
错因是unzip——命令没有找到，其原因肯定是没有安装unzip，安装unzip:
```base
yum install -y unzip zip
```



