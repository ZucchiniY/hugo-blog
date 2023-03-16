---
title: "demjson 报错 use_2to3 is invalid"
author: ["夏南瓜"]
date: 2023-03-16T00:00:00+08:00
lastmod: 2023-03-16T19:30:00+08:00
series: ["Python"]
tags: ["python3", "setuptools", "demjson"]
categories: ["开发"]
draft: false
---

今天在配置 Python3 环境时，安装 demjson 2.2.4 出现以下报错：

```shell
error in demjson setup command: use_2to3 is invalid
```

查看了一下报错的位置，发现是由于 demjson 2.2.4 兼容 Python2 和 Python3 ，当安装环境为 Python3 时，有一部分代码需要做相应的转换, 而 Setuptools 从版本 58.0.0 开始不再支持 2to3 的 builds ，所以导致 demjson 2.2.4 安装后不再可用，需要降级 setuptools 版本即可解决

```shell
pip install --upgrade setuptools==57.5.0
```
