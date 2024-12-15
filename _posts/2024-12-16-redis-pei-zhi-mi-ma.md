---
layout: post
title: redis配置密码
---
在redis目录中，修改```redis.windows.conf```文件
修改

```
requirepass password
```

然后，先启动```redis-server.exe```，再启动```redis-cli.exe```，输入

```
config set reqiurepass "password"
AUTH password
```

如果返回
```
OK
```
表明设置密码成功