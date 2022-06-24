---
title: 'Windows系统添加ssh-add'
date: 2022-04-24 20:24:08
tags: []
published: true
hideInList: false
feature: 
isTop: false
---
* 在git bash命令行输入
```
exec ssh-agent bash
eval ssh-agent -s
ssh-add "路径"
```