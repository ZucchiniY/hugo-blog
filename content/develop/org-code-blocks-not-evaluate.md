---
title: "Org Mode 导出时不执行代码段"
author: ["夏南瓜"]
date: 2023-02-21T00:00:00+08:00
lastmod: 2023-02-21T16:49:23+08:00
series: ["org-mode"]
tags: ["org-mode", "org-export-use-babel"]
categories: ["org-mode"]
draft: false
---

Org Mode 在绘制大量图片时，每次导出都会调用程序执行，会比较慢，所以希望可以在导出时，不主动运行代码。

查了一下，可以在代码段上增加 `:eval never-export` 来控制某一个代码版本不执行。

```org
#+begin_src plantuml :file export-not-eval-code.png :results output :cmdline -charset utf-8 :exports both :eval never-export
  @startmindmap
  ,* Linux
  ,** Suse Linux
  ,** Ubuntu
  ,** Debian
  @endmindmap
#+end_src
```

这个方法不错，但是如果想指定整个文件都不执行，则需要用到 `org-export-use-babel` 设置为 nil 来控制。

> 在 Org Mode 9.1 之前，可以设置 `org-export-babel-evaluate` 来跳过执行，但是 9.1 版本之后，这个参数就换成了 `org-export-use-babel` 。

如果是对整个文件来控制不做导出，则增加 `#+PROPERTY: header-args :eval never-export` 。

同样的，如果是仅对某个 header 控制，则可以增加 `:PROPERTIES:`


## properties {#properties}

```org
* header
:PROPERTIES:
:header-args: :eval never-export
:END:
```

配置后，这个标题下的内容就不再执行了。


## 未成功方法 {#未成功方法}

Org Mode 官方文本说可以通过 `#+BIND:` 来控制不自动执行。

需要先设置 `org-export-allow-bind-keywords` 为 `non-nil` ，然后在文件中增加 `#+BIND: export-babel-use-babel nil` 但是配置后并未启作用。
