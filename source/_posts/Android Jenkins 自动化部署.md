---
title: Android jenkins 自动化部署
date: 2018-04-27 16:40:00
tags: Android jenkins
---

==ps:首先重要的条件是有一台已经装好jenkins服务器 具体安装jenkins到服务器请参考[这里](https://www.cnblogs.com/h--d/p/5673085.html) ==

### 首先在jenkins上做好准备工作，那就是装插件 ###

系统管理-> 插件管理
![image](http://note.youdao.com/yws/res/1114/45DF43AFAD8F458F8C657587E8AFC2B6)

**装好github、gradle等插件**

1. 第一步新建：
 在Jenkins服务器上新建任务，取一个响亮的名字，选择构建一个自由风格的软件项目，轻轻的点击确定按钮，任务就建好了，系统自动进入Jenkins任务配置页面

2. 第二步配置：
添加描述；源码管理，添加路径，添加用户密码，添加分支（记得装github插件）；
![image](https:///note.youdao.com/yws/res/1105/D66A4D151FA5400E9F71864AF6E02D62)

3. 第三步构建项目触发器：
在你的gogs项目仓库设置中管理web钩子
![image](https:////note.youdao.com/yws/res/1192/A0F08A3BF29440F4B4A458D358FF5D76)

4. 第四步构建：
现在android的项目是用gradle构建，所以要选择invoke gradle script （记得先装gradle插件）
![image](https://note.youdao.com/yws/res/1108/7044307C7AD0468D8FD9BB89DFDDA312)

5. 添加一个execute shell 

```
#如执行打包命令 到command
./gradlew assebleDebug/assembleRelease
```

![image](https://note.youdao.com/yws/res/1120/06F5093ABC024C6287E493F86A445698)

6. 接下来添加你要上传的平台（例如蒲公英）（记得装蒲公英插件）[教程](https://www.pgyer.com/doc/view/jenkins_plugin)
![image](https://note.youdao.com/yws/res/1129/BB3372B237A34270BB2C0036FB34ED6A)

7. 接下来在添加一个excute shell 可以进行通知，（比如说钉钉机器人）
![image](https://note.youdao.com/yws/res/1140/9810A2C7743249F7955600269CE495C1)

**==就此完成。看似简单但是也有很多坑：==**

1. 要在jenkins服务器上把环境变量弄好，ANDROID_HOME,JAVA_HOME,GRADLE_HOME
首先：http://dl.google.com/android/android-sdk_r24.4.1-linux.tgzSDK
然后：配置环境变量linux下（/etc/profile）
 
```
export ANDROID_HOME='/opt/android-sdk-linux'  
export PATH=$ANDROID_HOME/tools:$PATH  
export PATH=$ANDROID_HOME/platform-tools:$PATH  
```

2. 安装android sdk 所有的包

    
    ```
    android update sdk --no-ui
    ```
    
    这样太占内存也可以使用 
    
    ```
    sdkmanager "platform-tools" "platforms;android-26"
    
    sdkmanager  "build-tools;26.0.2"
    ```
    下载指定的包，节省空间
    也可以使用
    ```
    android list
    ```
     sdk命令查看有哪些包更新，然后通过
    $ ./android  update sdk -u -t  序号
    如：安装Build-tools, revision 24.0.3
    
    ```
    $ ./android update sdk -u -t 3
    ```
    需要同意license，输入 y 回车即可