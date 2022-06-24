---
layout: post
title: Windows系统添加ssh-add
---
* 在git bash命令行输入
```
exec ssh-agent bash
eval ssh-agent -s
ssh-add "路径"
```