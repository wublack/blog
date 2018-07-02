---
title: Hexo 快速构建属于你自己的blog
date: 2017-05-04 18:09:22
tag: Hexo
---

博客这个东西，很早就想弄一下了今天弄一个玩玩

## 第一步 环境配置篇

### 安装node环境  可查看[node](https://node.org)

 **以linux系统为例：**
 
我这里使用的 <font color=#FF0000 size=6 >nvm</font> node版本管理器
- 首先下载nvm
``` bash
    wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh | bash
```  

安装完成之后
+ 配置nvm环境变量
``` bash
    vim ~/.bash_profiles
``` 

+ 粘贴线代码到文件末尾
``` bash
    export NVM_DIR="$HOME/.nvm"
    [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh" # This loads nvm
``` 

+ 执行 生效环境变量
``` bash
    source ~/.bash_profiles
``` 

### 验证 <font color=#FF0000 size=6 >nvm</font> 是否安装成功    
+ 执行nvm
``` bash
    $ nvm --verion
    0.33.0
``` 
打印版本号，说明安装成功
+ 安装node
```bash
#查看当前所有的node版本
nvm ls-remote
#选择一个安装
nvm install v8.9.0
```

### 在本地安装  [hexo](https://hexo.io)[详情可以参考这个网站]
```bash
    #全局安装hexo脚手架
    npm install hexo-cli -g
```

## 博客构建篇

### 创建一个项目

``` bash
$ hexo new "My New Post"
```

更多信息可[参考](https://hexo.io/docs/writing.html)

### 运行hexo服务

``` bash
$ hexo server
```

更多信息可[参考](https://hexo.io/docs/server.html)

### 生成博文静态文件

``` bash
$ hexo generate
```

更多信息可[参考](https://hexo.io/docs/generating.html)

### 部署文件到你的git

``` bash
$ hexo deploy
```

更多信息可[参考](https://hexo.io/docs/deployment.html)
