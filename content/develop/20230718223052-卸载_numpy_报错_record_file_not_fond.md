---
title: "卸载 numpy 报错 RECORD file not fond"
author: ["夏南瓜"]
date: 2023-07-18T00:00:00+08:00
lastmod: 2023-07-18T22:40:55+08:00
series: ["python"]
tags: ["numpy", "RECORD file not fond"]
categories: ["开发"]
draft: false
---

更新回测程序的时候，numpy 报错信息如下：

```text
WARNING: Error parsing requirements for numpy: [Errno 2] No such file or directory: '/usr/local/Caskroom/miniconda/base/envs/backtrader/lib/python3.9/site-packages/numpy-1.24.1.dist-info/METADATA'
```

想通过更新 numpy 或者先卸载再重新安装，但是操作的时候，报错：

```shell
ERROR: Cannot uninstall numpy 1.24.1, RECORD file not found. You might be able to recover from this via: 'pip install --force-reinstall --no-deps numpy==1.24.1'.
```

查了一下，按下面的方案可以更新：

1.  找到 python packages 的地址
    ```shell
    SITE_PACKAGES_FOLDER=$(python3 -c "import sysconfig; print(sysconfig.get_paths()['purelib'])")
    echo $SITE_PACKAGES_FOLDER
    ```
    查看一下 numpy 的内容：
    ```shell
    ls $SITE_PACKAGES_FOLDER/numpy*
    ```

2.  然后安装 trash-cli 包，删除对应的内容
    ```shell
    pip install trash-cli
    trash $SITE_PACKAGES_FOLDER/numpy*
    ```

<!--listend-->

1.  最后更新 numpy 包
    ```shell
    pip install --upgrade numpy
    ```
