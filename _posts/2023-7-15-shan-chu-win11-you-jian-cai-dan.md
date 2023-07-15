---
layout: post
title: 删除win11右键菜单
---
### 切换到旧版右键菜单：

```reg add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /f /ve```

### 恢复回Win11右键菜单：

```reg delete "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}" /f```

### 重启Windows资源管理器生效：

``` taskkill /f /im explorer.exe & start explorer.exe```