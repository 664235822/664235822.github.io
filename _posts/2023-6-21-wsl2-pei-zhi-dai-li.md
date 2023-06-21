---
layout: post
title: wsl2配置代理
---
### windows v2ray客户端开启允许来自局域网的连接
### 在~/.bashrc中添加如下内容

```
export hostip=$(ip route | grep default | awk '{print $3}')
export hostport=10811
alias proxy='
    export HTTPS_PROXY="http://${hostip}:${hostport}";
    export HTTP_PROXY="http://${hostip}:${hostport}";
    export ALL_PROXY="http://${hostip}:${hostport}";
    echo -e "Acquire::http::Proxy \"http://${hostip}:${hostport}\";" | sudo tee -a /etc/apt/apt.conf.d/proxy.conf > /dev/null;
    echo -e "Acquire::https::Proxy \"http://${hostip}:${hostport}\";" | sudo tee -a /etc/apt/apt.conf.d/proxy.conf > /dev/null;
'
alias unproxy='
    unset HTTPS_PROXY;
    unset HTTP_PROXY;
    unset ALL_PROXY;
    sudo sed -i -e '/Acquire::http::Proxy/d' /etc/apt/apt.conf.d/proxy.conf;
    sudo sed -i -e '/Acquire::https::Proxy/d' /etc/apt/apt.conf.d/proxy.conf;
'
```

### 重启wsl2
### 使用代理 
```proxy```
### 取消代理
```unproxy```
### 测试代理
```curl www.google.com```