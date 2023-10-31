---
title: "hugo 报错 rss.xml 找不到 email"
author: ["夏南瓜"]
date: 2023-10-31T00:00:00+08:00
lastmod: 2023-10-31T15:09:09+08:00
series: ["hugo"]
tags: ["hugo", "rss", "email"]
categories: ["开发"]
draft: false
---

服务器上的博客更新了一篇文章，但是在生成博客资源时，报错：

```text
ERROR render of "section" failed: template: _internal/_default/rss.xml:3:9: executing "_internal/_default/rss.xml" at <site>: can't evaluate field email in type string
```

但是查看配置文件和 theme 的代码，并没有发现问题。到 hugoio 的论坛中找了一下，发现是配置文件中没配置对应的 email 信息导致的。

新的配置文件如下：

```yaml
author:
  name: name
  email: xxxxxx@xxx.com
```

再重新生成即可。
