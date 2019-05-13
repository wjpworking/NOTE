---
title: SSH 使用问题汇总
prev: false
next: false
sidebar: auto
---

## 一. 提示 `Broken pip`

这个时候在`~/.ssh/config`中加入如下的配置：

``` bash
Host *
  ServerAliveInterval 120
  IPQoS=throughput
```

## 二. `PTY allocation request failed on channel 0`

`PTY`是一个伪终端，提示为伪终端分配失败，然后提示成功后输出欢迎信息，最后连接被关闭了。这是因为基于`SSH`的`Git`不需要一个tty，所以被拒绝分配成一个`tty`接入站点，这个时候使用`ssh -T`就行