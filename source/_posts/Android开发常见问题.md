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
4. Android 颜色透明值列表
![image](http://note.youdao.com/noteshare?id=20681fb6df01851fe8ea60d402f99503&sub=WEB4ec96fecb271d9675b9402a181090220)

5. Android 一个键盘监听变化[框架](https://github.com/18511084155/KeyboardWatcher)

6. Android build项目的时候Re-download dependencies and sync project (requires network)
    解决方法：
    + 第一种方法删除.gradle文件夹
    ![image](http://note.youdao.com/noteshare?id=889dfd7dbf849b1f26470c6b55d921c8&sub=234C405A59BE465686F4183B84502171)
    + 第二种方法修改项目中gradle-wrapper.properties gradle版本

7. Android 对TextView进行各种操作SpannableString 这个类很神奇详情请百度

8. Android 一个封装的很不错的pupwindow组件[库](https://github.com/crazyqiang/AndroidStudy/tree/master/app/src/main/java/org/ninetripods/mq/study/popup)