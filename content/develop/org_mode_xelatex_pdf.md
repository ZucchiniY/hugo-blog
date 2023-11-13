---
title: "org mode Latex 编辑"
author: ["夏南瓜"]
date: 2023-11-13T00:00:00+08:00
lastmod: 2023-11-13T15:27:50+08:00
series: ["emacs"]
tags: ["orgmode", "xelatex", "pdf"]
categories: ["开发"]
draft: false
---

## 安装 LaTex 编译工具 {#安装-latex-编译工具}

在 Mac 上仅需要使用 brew 命令直接安装即可。

```shell
brew install baisctex
```


## 语法特点 {#语法特点}

需要对公式使用 `$$...$$` 进行包裹，如果是希望在行内使用公式，则使用 `$... $` 进行包裹，即 \\(AA = \frac{\mbox{中文}}{\mbox{测试}}\\)

\\[AA = \frac{\mbox{中文}}{\mbox{测试}}\\]


## 在 org mode 中预览 {#在-org-mode-中预览}

basictex 仅有基础内容，需要安装正面的包，才能正常生成 pdf 。

```shell
sudo tlmgr install capt-of
sudo tlmgr install wrapfig

sudo tlmgr install nth
sudo tlmgr install ulem xcolor environ letltxmacro enumitem stringenc trimspaces soul algorithm2e genmisc
sudo tlmgr install epstopdf subfigure appendix

sudo tlmgr install ifmtarg
sudo tlmgr install multirow ifoddpage relsize titlesec
sudo tlmgr install xifthen
```

然后需要在导出文件中，增加头文件：

```org
#+latex_cmd: xelatex
#+LATEX_HEADER: \usepackage{fontspec}
#+LATEX_HEADER: \setmainfont{PingFang SC}
```
