---
title: Android gradle 下载目录更改
date: 2018-05-22 10:38:22
tags: Android gradle
---

### 通常我们gradle下载目录在用户下面例如window在user/admin/.gradle目录下，###
### 但是这个gradle可能项目不一样，下载的gradle本  也不一样就会导致C盘内存空间减少，那有啥好办法没呢 ###
### 答案肯定是有的 ###

在你项目的gradle.properties文件下添加一句

```
gradle.user.home=D:/Cache/.gradle 
```

但是这也有个缺点就是每个项目都要加。