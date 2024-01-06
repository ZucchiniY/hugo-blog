---
title: "lxml 包安装"
author: ["夏南瓜"]
date: 2024-01-06T00:00:00+08:00
lastmod: 2024-01-06T17:49:57+08:00
series: ["python"]
tags: ["lxml", "libxml2", "libxslt"]
categories: ["开发"]
draft: false
---

在测试爬虫的时候，报错找不到对应的 lxml 包，直接使用 `pip install lxml` 安装，再执行还是有类似的问题，查了一下，说是需要从 lxml 官方网站下载安装才可以。

直接下面官方的源码：

```shell
git clone https://github.com/lxml/lxml.git lxml
```

因为我是使用 conda 管理开发环境的，所以切换到对应的环境后，直接使用 `pip install lxml/` 安装，提示需要安装 libxml2 和 libxslt 。

使用 `sudo apt install libxml2-dev libxslt-dev python-dev-is-python3` 命令安装对应的 CPython 包后，再执行 `pip install lxml/` 即可成功安装。
