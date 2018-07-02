---
title: Flutter 初识
date: 2018-04-10 20:51:38
tags: 混合开发
---

Flutter google为了更方便的实现跨平台的 material design 和高性能的渲染移动应用开发而的混合开发框架
### Flutter 特性：
1.Fast Development
2.Expressive, beautiful UIs
3.Modern, reactive framework

### Flutter入门

作为一个移动开发者，不去了解新出来的混合开发框架是不合适的。今天我们就来看看大google的Flutter混合框架吧。

1. 做开发当然第一步当然是配置开发环境：
    + clone flutter项目
    ```
        git clone -b beta https://github.com/flutter/flutter.git
    ```
    + 然后在设置环境变量（这个我就不说怎么设置环境变量了）
    + 运行flutter doctor 要安装（SDK,Dart插件，Flutter插件，连接一台Android机）
    ```
        flutter doctor
        #他会提示你有哪些环境没有配置好，你可根据他的提示一步步找问题
    ```
    ==关于Android sdk最好是下载一个新的，如果是老的，会有很多问题==
    
    最后如果flutter doctor 都没有问题了，说明环境变量配置成功。
    
2. 在安装Dart和Flutter插件之后，就可以在Android studio新建一个Flutter项目
![image](https://www.wl52056.top/images/flutter_blog_back34123.png)

3. 创建完之后，就可以运行Flutter项目啦
   ![image](https://www.wl52056.top/images/blog_flutter_backq34134.png)

4. 完成