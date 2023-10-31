---
title: "orbstack 工具"
author: ["夏南瓜"]
date: 2023-10-31T00:00:00+08:00
lastmod: 2023-10-31T12:04:00+08:00
series: ["mac"]
tags: ["orbstack", "docker"]
categories: ["开发"]
draft: false
---

orbstack 是在 Mac 环境上使用，可以替代虚拟机的工具，可以非常容易的安装 docker 镜像、Linux 镜像，而且是开源工具，已经被收录到 homebrew cask 仓库，可以使用 brew 命令进行安装。

```shell
brew install orbstack --cask # 安装 orbstack
brew upgrade --greedy orbstack # 升级 orbstack
```

最主要的优势是轻量、启动快、占用资源少，对于寸土寸金的 Mac 电脑来说，这是非常重要的。

使用 docker 镜像的命令也与 docker 原生方式一致。

```shell
docker compose -p penpot -f docker-compose.yaml up -d
```

这样就可以在 Mac 上轻松的使用 docker 建立虚拟机了。

另外 orbstack 还提供了其他命令来管理：

```shell
orbctl help # 查看帮助
orb create ubuntu ci-runner # 创建 ubuntu 虚拟机
```

另外可以使用命令来启停容器：

```shell
orb # or orb start
orb stop # 停止容器
orb config # 修改 orb 配置
orb restart docker # 重启 docker 镜像
orb list # 查看虚拟机列表
```
