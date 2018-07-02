---
title: git clone时出现 error:inflate:data stream error(incorrect data check)
date: 2018-07-1 17:50:38
tags: git
---

1. 最近在Mac上git clone服务器上的项目时，不管怎么样都clone不下来就算100%也会报错，内容如下

```
remote: Counting objects: 11326, done.
remote: Compressing objects: 100% (7538/7538), done.
remote: Total 11326 (delta 5828), reused 7632 (delta 3000)
Receiving objects: 100% (11326/11326), 153.66 MiB | 258.00 KiB/s, done.
error: inflate: data stream error (incorrect data check)
fatal: serious inflate inconsistency
fatal: index-pack failed
```
其实原因很简单，但是因为你的git 版本太低了!~！解决方法：
==利用brew 安装一个最新的git就行了==如果没有安装brew可[参考](https://brew.sh/index_zh-cn)
```
#复制这个命令执行即可
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
2. 安装完成之后,执行
```
brew unlink git 
```
3. 然后在执行，下面的命令
```
brew install git
```
执行完成之后，会提示安装版本和安装路径

最后把安装路径替换环境变量~/.bash_profile文件，执行
```
export PATH="/usr/local/git/bin:$PATH"
```
4. 然后执行source ~/.bash_profile ，立即生效

5. 然后新打开一个终端执行git命令就可以了。


