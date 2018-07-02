---
title: React-Native与Android原生混合开发交互
date: 2017-07-20 21:38:22
tags: Android React-Native
---

1. 首先用Android Studio 创建一个正常的Android项目，最低版本改成4.1
2. 确定安装npm后
    ```
    npm init
    ```  
    然后通过
     ```
    npm install --save react react-native
     ```
3. 在项目目录下下载.flowconfig 地址https://raw.githubusercontent.com/facebook/react-native/master/.flowconfig （可通过curl下载）

4. 在package.json添加 "start":"node node_modules/react-native/local-cli/cli.js start"

5. 在安装应用之后，打不开react-native页面报（Uable to load script form assets 'index.androlid bundle'.Make sure your bundle is packaged correctly or you`re running a packager server.）
解决的方法：把 node_modules/react-native/local-cli/server/server.js 代码 （process.exit(11)）注释

6. 添加index.android.js文件到项目目录下写react-native代码

7. 在app->build.gradle下添加react-native依赖包compile "com.facebook.react:react-native:+"

8. 在项目下build.gradle ->allprojects ->repositories ->maven 添加 
url "$rootDir/node_modules/react-native/android"

9. 在AndroidManifest.xml添加Internet权限，访问网络必须

10. 创建一个activity继承ReactActivity重写getMainComponetName方法 
返回 在index.android.js中 （AppRegister.registerComponent('HelloWorld) =>HelloWorld）
中注册的名字

11. 创建MyApplication 继承Application 实现接口ReactApplication 实现getReactNativeHost