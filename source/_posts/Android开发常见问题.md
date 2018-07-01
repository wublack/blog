---
title: Android 常见问题
date: 2018-05-22 10:38:22
tags: Android
---

1. 常常在gradle编译时，出现异常，但是打印的异常信息较少不能准确定位到底是哪里有问题可执行如下命令：
````
 gradlew processDebugManifest --stacktrace
````

2. 查看当前activity
````
 adb shell dumpsys activity activities
````

3. Android Gson 对象Map转换 [参考](https://www.cnblogs.com/zsychanpin/p/6937832.html)
````
 JSONParse pare = new JSONParse();
````
4. Android gradle 下载目录更改
