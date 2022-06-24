---
title: 'git配置代理'
date: 2022-04-24 20:23:43
tags: []
published: true
hideInList: false
feature: 
isTop: false
---
* 设置socks代理
```
git config --global http.proxy 'socks5://127.0.0.1:1080'
git config --global https.proxy 'socks5://127.0.0.1:1080'
```
* 设置https代理
```
git config --global https.proxy http://127.0.0.1:1080
git config --global https.proxy https://127.0.0.1:1080
```
* 取消代理
```
git config --global --unset http.proxy
git config --global --unset https.proxy
```