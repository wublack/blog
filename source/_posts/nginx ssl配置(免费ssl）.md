
---
title: nginx ssl配置（免费ssl）
date: 2018-06-29 11:09:22
tags: nginx linux
---
# nginx ssl配置（免费ssl）
### ==强烈建议有钱人使用付费ssl==

1. 首先在[freessl](https://freessl.org)官网注册账号

1. 然后在首页输入你的网站地址 点击创建  ![image](https://www.wl52056.top/images/blog_201806_back1.png)


1. 点击把文件下载，把下载下来的文件放到提示的目录下面('.well-known/pki-validation')  ![image](https://www.wl52056.top/images/blog_back_201806123.png)  ==ps:能复制就不要手写 ==

    ==ps:记得关闭防火墙，开放端口，在这里我是浪费了很多时间，nginx记得配置txt能访问到==
    
>     firewall-cmd  --zone=public --add-port=80/tcp

1. 最后点击验证。通过之后会提供证书压缩文件给你下载  ![image](https://www.wl52056.top/images/blog_nginx_config_back221.png)
 
1. 最最后配置你的nginx

```
server {
  listen 80;
  listen 443 ssl http2;
  ssl_certificate /usr/local/nginx/conf/ssl/app.wl52056.top.pem;
  ssl_certificate_key /usr/local/nginx/conf/ssl/app.wl52056.top.key;
}
```
1. 验证一下访问你配置的域名

   ![image](https://www.wl52056.top/images/blog_nginx_back_https234.png)
  访问成功,说明配置成功
