---
title: Vue 初探
date: 2017-06-22 10:50:38
tags: Vue
---

###### 因为公司为了更好的适应快速迭代开发和避免Apple Store 审核决定使用Vue和原生混合开发，把公司重要的，变动较大的流程部分用Vue来进行开发为此==让我们来认识一下Vue 吧==

1. 为什么要选择vue.js来作为混合开发呢？让我们来看看他的优点吧！

    -  vue.js上手比较简单，只要有点前端html知识的人，都能很容易上手
    -  可高度组件化，复用性高，开发快捷
    -  vue.js本身比较轻便，不像react和AngularJS过于沉重复杂，（==对我们这种做原生应用的前端小白来说啊==）
    -  最后就是给予weex较大期望，以后方便通用。快速移植

1. 首先vue.js的中文[官网](https://cn.vuejs.org/v2/guide/index.html)
    
    ~~vue.js它不支持IE8及以下的浏览器，如果要兼容一些古董类型浏览器的，vue.js就不是你的菜了，可以考虑[avalon](http://avalonjs.github.io/)~~

2. 打开cmd终端 安装vue-cli脚手架工具

```
#安装脚手架工具
npm install vue-cli -g

#新建初始化项目
D:\workspace> vue init webpack my-project

  A newer version of vue-cli is available.

  latest:    2.9.6
  installed: 2.9.2

? Project name my-project
? Project description A Vue.js project
? Author Tim <wl52056@163.com>
? Vue build standalone
? Install vue-router? Yes
? Use ESLint to lint your code? Yes
? Pick an ESLint preset Standard
? Set up unit tests No
? Setup e2e tests with Nightwatch? Yes
? Should we run `npm install` for you after the project has been created? (reco
mmended) npm

   vue-cli · Generated "my-project".


# Installing project dependencies ...
# ========================

npm WARN deprecated socks@1.1.10: If using 2.x branch, please upgrade to at leas
t 2.1.6 to avoid a serious bug with socket data flow and an import issue introdu
ced in 2.1.0

> chromedriver@2.40.0 install D:\workspace\my-project\node_modules\chromedriver
> node install.js

Downloading https://chromedriver.storage.googleapis.com/2.40/chromedriver_win32.
zip
Saving to C:\Users\admin\AppData\Local\Temp\chromedriver\chromedriver_win32.zip
Received 781K...
Received 1575K...
Received 2359K...
Received 3143K...
Received 3376K total.
Extracting zip contents
Copying to target path D:\workspace\my-project\node_modules\chromedriver\lib\chr
omedriver
Done. ChromeDriver binary available at D:\workspace\my-project\node_modules\chro
medriver\lib\chromedriver\chromedriver.exe

> uglifyjs-webpack-plugin@0.4.6 postinstall D:\workspace\my-project\node_modules
\webpack\node_modules\uglifyjs-webpack-plugin
> node lib/post_install.js

npm notice created a lockfile as package-lock.json. You should commit this file.

npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.4 (node_modules\fse
vents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@
1.2.4: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"}
)

added 1414 packages in 121.681s


Running eslint --fix to comply with chosen preset rules...
# ========================


> my-project@1.0.0 lint D:\workspace\my-project
> eslint --ext .js,.vue src test/e2e/specs "--fix"


# Project initialization finished!
# ========================

To get started:

  cd my-project
  npm run dev

Documentation can be found at https://vuejs-templates.github.io/webpack



D:\workspace>cd my-project && npm run dev
 DONE  Compiled successfully in 3470ms                                  14:35:32

 I  Your application is running here: http://localhost:8080
  
```
感觉就是一路的回车，然后就。。。
说明整个创建vue项目已经成功，然后就在浏览器打开http://localhost:8080


.vue文件的template标签下写html代码

在script写你的javascript代码，
```bash
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Hello World'
    }
  }
}
```
style下尽情的写你那牛逼的特效