---
title: 手把手搭建一个免费的Vpn
date: 2018-01-02 14:40:00
tags: vpn
---
# 手把手教你弄一个免费一年的VPN翻墙服务

作为一个开发人员，都知道百度搜索的坑，所以都想使用Google来搜索一些问题，毕竟国外大神也是挺多的。但是Google因为在2012就已经退出中国市场，访问免不了要一个翻墙利器。今天我来给大家介绍怎么弄个免费一年的翻墙服务吧！

### 一、首先自己能翻墙访问Google。
那有人就说了，我既然能翻墙了，还要你那个干嘛，这样说的好像很有道理样子，你可以出门右转了。其实呢，我们这个翻墙只是为了能获取这个免费的一年的翻墙服务的一个先决条件，可以听我细细道来：

你可以先在网上找一个收费的，但一般都会有免费试用，打个譬如[蓝灯](https://getlantern.org/zh_CN/)

打开蓝灯，一般都会有一个月300M的试用流量，你电脑的右下边就会出现他的图标,你就可以使用了，（有的时候网络可能不太好，但是没有关系，它总会好的，@~@）确定自己能翻墙之后

### 二、需要一张visa或者mastercard
因为它会验证你的信用卡是否真实有效，会扣款1美元，然后又会返回给你，所以不用担心

### 三、打开 cloud.google.com
- 如果你有google账号，最好了，直接登录，没有呢，那没办法了，注册一个呗，反正免费注册的，注册这种东西，我就不赘述了，你们自行百度。

- 接着你会发现有一个免费试用按钮，点击免费试用，它会让你填写一些你的信息，直接填写就好了，然后你就是让你填写你的信用卡信息就好了，然后就成功了，它会跳转到这个页面
![image](https://wl52056.top/images/vpn_service_back134.png)
说明一切正常
- 然后点击左上角，选择Compute 选择vm实例，新建一个实例。如图：
![image](https://wl52056.top/images/blog_vpn_back12341234.png)
点击上边的创建实例，配置选择可参考我的，如图：
![image](https://wl52056.top/images/blog_vpn_back344234.png)
==因为只是做一个vpn服务器，不需要多高的配置，没必要浪费==
- 创建成功之后你的VM实例列表中就会有多个实例，点击ssh,在浏览器打开
![image](https://wl52056.top/images/blog_vpn_back4545245.png)

1. 输入命令：
```
sudo -i
```
切换到root用户下面。
2. 安装bbr
```
wget -N --no-check-certificate https://raw.githubusercontent.com/FunctionClub/YankeeBBR/master/bbr.sh && bash bbr.sh install
```
蓝底窗口按TAB键选NO

选择重启 Y

这里会断开连接，大家可以关掉窗口再重新打开或几秒钟后在界面随便按几个字母 便会提示重新连接。
3. sudo -i 再次切换到root用户下边
4. 启动bbr
```
bash bbr.sh start
```
5. 获取ssr脚本
```
wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocksR.sh && chmod +x shadowsocksR.sh
```
6. 执行ssr脚本
```
./shadowsocksR.sh
```
输入shadowsocks 密码

输入**端口号**

其他一路回车（也可自行选择混淆 协议）

在最后出现红底数据以后,

7. 去谷歌云防火墙规则添加新的防火墙规则
![image](https://wl52056.top/images/blog_vpn_back45o0452.png)
如图：
![image](https://wl52056.top/images/blog_vpn_back20180703162421.png)
填入你自己定义的端口号，类似tcp;udp:5665

8. 然后就可以自己去下载一个客服端测试是否可用啦

[mac下载地址](https://github.com/qinyuhang/ShadowsocksX-NG-R/releases)

[pc下载地址](https://github.com/shadowsocksrr/shadowsocksr-csharp/releases)

[Android下载地址](https://wl52056.top/images/ssr-android.apk)

iOS下载地址必须有一个非大陆的appleid才行，Apple Store下载wingy就行了

9. 运行ssr软件，右击服务器设置/编辑服务器，添加自己的翻墙服务器地址，端口，密码，混淆规则到shadowsocksrr客服端
![image](https://wl52056.top/images/blog_vpn_back20180703163234.png)
10. 右击小飞机选择服务器，选择你自己添加的服务器，还可以选择代理模式和代理规则。然后就可以啦。