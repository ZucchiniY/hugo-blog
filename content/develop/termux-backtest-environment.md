---
title: "Termux 安装回测环境"
author: ["夏南瓜"]
date: 2023-03-06T00:00:00+08:00
lastmod: 2023-03-06T19:47:47+08:00
series: ["backtrader"]
tags: ["termux", "手机回测环境"]
categories: ["开发"]
draft: false
---

如果想在安卓手机上配置一套量化的回测环境的话，一般是什么 Termux 来安装 Python 环境。

首先需要安装 lxml

```shell
apt install libxml2 libxslt
```

然后，安装 pandas

```shell
export CFLAGS="-Wno-deprecated-declarations -Wno-unreachable-code"
pip install pandas
```

安装pillow

```shell
apt install libjpeg-turbo libpng
pip install pillow
```

安装matplotlib

```shell
apt install libpng freetype numpy scipy
pip install wheel
pip install kiwisolver
pip install matplotlib
```

安装akshare用来获取股票数据

```shell
pip install akshare
```

安装backtrader回测工具

```shell
pip install backtrader
```

> 但是需要注意的是， numpy==1.19.3 ，matplotlib==3.2.2 要使用固定的版本，不然不能启动回测程序。
