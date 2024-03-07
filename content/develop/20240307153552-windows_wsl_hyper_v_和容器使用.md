---
title: "windows wsl hyper-v 和容器使用"
author: ["夏南瓜"]
date: 2024-03-07T00:00:00+08:00
lastmod: 2024-03-07T16:15:55+08:00
series: ["windows"]
tags: ["hyper-v", "docker", "docker-desktop"]
categories: ["开发"]
draft: false
---

## 家庭版 windows 开启 hyper-v {#家庭版-windows-开启-hyper-v}

家庭版的 windows11 默认无法设置 hyper-v ，需要执行下面的脚本，安装对应的模块才可以。

脚本如下，保存为 **.cmd** 或者 **.bat** 文件，然后使用管理员角色运行即可。

```shell
pushd "%~dp0"
dir /b %SystemRoot%\servicing\Packages\*Hyper-V*.mum >hyper-v.txt
for /f %%i in ('findstr /i . hyper-v.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"
del hyper-v.txt
Dism /online /enable-feature /featurename:Microsoft-Hyper-V-All /LimitAccess /ALL
```


## 容器资源占用管理 {#容器资源占用管理}

在使用过程中发现容器本身占用近 7G 内存，40% CPU，导致系统整体性能下降的厉害，排查了一下，可以通过 **.wslconfig** 文件控制 docker 容器的体积。

```shell
[wsl2]
memory=2GB
processors=4
swap=2GB
```

配置好参数后，重启容器即可。再打开发现容器的资源占用就比较合理了。


## 常用容器使用命令 {#常用容器使用命令}

```shell
# 查看容器
docker ps

# 登录容器
dockter attach docker_name
dockter exec -it docker_name /bin/bash

# 查看容器
docker inpect docker_nam
```
