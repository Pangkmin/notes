### 准备 LAMP 环境
LAMP 是 Linux、Apache、MySQL 和 PHP 的缩写，是 Discuz 论坛系统依赖的基础运行环境。我们先来准备 LAMP 环境

#### 安装 MySQL
使用 yum 安装 MySQL：
```base
yum install mysql-server -y
```
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
初始密码为locald

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
