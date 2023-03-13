---
title: "安装 emacs-plus"
author: ["夏南瓜"]
date: 2023-03-13T00:00:00+08:00
lastmod: 2023-03-13T15:11:31+08:00
series: ["emacs"]
tags: ["brew_install_emacs-plus"]
categories: ["开发"]
draft: false
---

在 Mac 上使用 homebrew 命令安装工具非常方便，因为本人是重度的 Emacs 用户，一直使用的是 emacs-mac 的 Emacs，但是这里的 Emacs 版本其实是比较慢的，有时候希望可以自主选择安装的版本的 Emacs，这里我使用的是 emacs-plus 。

安装对应的 tap 库的方法是 `brew tap d12frosted/emacs-plus` 命令，然后选择安装 emacs-plus 29 版本进行安装，命令如下：

```shell
brew install emacs-plus@29 --with-xwidgets --with-imagemagick --with-cacodemon-icon
```

之后再为下载的 Emacs 包建立到 Applications 的链接：

```shell
ln -s /usr/local/opt/emacs-plus@29/Emacs.app /Applications
```

最后需要把 emacs 使用服务启动：

```shell
brew services restart d12frosted/emacs-plus/emacs-plus@29
```

这个库非常好用，缺点就是下载有点慢了，如果能[利用 brew 代理]({{< relref "20221010153245-为_brew_tap_使用代理地址.md" >}})来下载就更好了。
