---
title: Android 跨进程通讯
date: 2017-03-20 22:40:00
tags: Android
---

# Android 跨进程通讯

1. 首先新建一个自定义实体类：Person 实现 Parcelable 接口，

2. 新建一个与类名相同的aidl的文件，主要两个的包名必须相同，
   只写一句代码 parcelable Person;

3. 在新建一个aidl的文件（例：IManagerPerson.aidl） 在接口中使用 实体类 例：sendMessage(Person ps);
并import导入Person类的完整路径

4. 新建一个service 实现onCreate(),onStartCommand(),和onBind()方法
并且继承IManagerPerson.Stub重新sendMessage方法，在onBind()方法中return IManagerPerson.Stub的实例
在intent-filter设置action名字方便启动

5. 在Activity中使用：
实例一个ServiceConnection 实现onServiceConnected(),onSreviceDisconnected()
在onServiceConnected()方法中通过IManagerPerson.Stub.asInterface(service);
获取IManagerPerson实例，通过onbind启动service，记得unbindService,然后就可以通过
IManagerPerson跨进程调用方法