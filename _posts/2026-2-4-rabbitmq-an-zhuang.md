---
layout: post
title: RabbitMQ 安装
---
### 添加环境变量

```
C:\Program Files\RabbitMQ Server\rabbitmq_server-4.2.1\sbin
```

* 重启

### 修复命令问题

* 复制 
```
C:\Windows\System32\config\systemprofile\.erlang.cookie
```
* 到 
```
C:\Users\用户名\.erlang.cookie
```

### 启动管理页面

```
rabbitmq-plugins enable rabbitmq_management
```

* 端口 15672
* 默认账号 quest
* 默认密码 guest

### 新建用户

```
rabbitmqctl add_user myuser password
rabbitmqctl set_permissions -p / myuser ".*" ".*" ".*"
rabbitmqctl set_user_tags myuser administrator
```

### 启用远程访问

* 修改rabbitmq.conf
```
[
  {
    rabbit, 
    [
      {
        tcp_listeners, [5672]
      }, 
      {
        loopback_users, []
      }
    ]
  }
].
```