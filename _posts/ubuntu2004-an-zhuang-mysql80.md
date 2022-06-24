---
title: 'Ubuntu20.04安装MySQL8.0'
date: 2022-04-24 20:22:39
tags: []
published: true
hideInList: false
feature: 
isTop: false
---
### 安装MySQL8.0
```sudo apt-get install mysql-server```
### 执行安装脚本
```sudo mysql_secure_installation```
```
VALIDATE PASSWORD PLUGIN can be used to test passwords...
Press y|Y for Yes, any other key for No: N (我的选项)

Please set the password for root here...
New password: (输入密码)
Re-enter new password: (重复输入)

By default, a MySQL installation has an anonymous user,
allowing anyone to log into MySQL without having to have
a user account created for them...
Remove anonymous users? (Press y|Y for Yes, any other key for No) : Y (我的选项)

Normally, root should only be allowed to connect from
'localhost'. This ensures that someone cannot guess at
the root password from the network...
Disallow root login remotely? (Press y|Y for Yes, any other key for No) : N (我的选项)

By default, MySQL comes with a database named 'test' that
anyone can access...
Remove test database and access to it? (Press y|Y for Yes, any other key for No) : Y(我的选项)

Reloading the privilege tables will ensure that all changes
made so far will take effect immediately.
Reload privilege tables now? (Press y|Y for Yes, any other key for No) : Y (我的选项)
```
### 配置远程访问
```sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf```
注释掉
* ```bind-address = 127.0.0.1```
* ```imysqlx-bind-address = 127.0.0.1```
* 配置远程账户
```sudo mysql -uroot -p```
* 应先创建新用户
```create user 'root'@'%' identified by '密码';```
* 执行授权
```GRANT ALL PRIVILEGES ON *.* TO 'root'@'%';```
* 刷新
```flush privileges;```
* 授权远程
```ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY '密码';```
* 刷新
```flush privileges;```
### 重启mysql服务
```sudo systemctl restart mysql```