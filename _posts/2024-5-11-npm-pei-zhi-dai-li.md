---
layout: post
title: npm配置代理
---
### npm配置默认源

```
npm config set registry https://registry.npmjs.org/
```

### npm配置国内镜像源

```
npm config set registry http://registry.cnpmjs.org
```

### 在npm中配置代理

```
npm config set proxy http://127.0.0.1:10809
npm config set https-proxy http://127.0.0.1:10809
```

### 要检查配置是否成功

```
npm config get proxy
npm config get https-proxy
```

### 删除代理
```
npm config delete proxy
npm config delete https-proxy
```