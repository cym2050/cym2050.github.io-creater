---
title: "macOS终端开启代理"
date: 2020-04-07T19:15:13+08:00
draft: false
---

默认你本地已有可以访问404的代理

设置代理
```
export http_proxy="http://127.0.0.1:1086"
export https_proxy="http://127.0.0.1:1086"
export all_proxy="socks5://127.0.0.1:1086"
```
取消代理
```
unset http_proxy
unset https_proxy
unset all_proxy
```