---
title: linux tomcat虚拟主机配置
date: 2018-06-29 11:09:22
tags: linux tomcat
---

# tomcat虚拟主机配置
1. 安装好[tomcat](http://tomcat.apache.org//) [nginx](http://www.nginx.cn/doc/) 搭建好Java开发环境 也可参照[onestack](https://oneinstack.com/auto/)一键搭建。如图：
![image](https://www.wl52056.top/images/blog_tomcat_backq2341.png)

2. 一键添加虚拟主机

```
./vhost.sh

#######################################################################
#       OneinStack for CentOS/RadHat 6+ Debian 7+ and Ubuntu 12+      #
#       For more information please visit https://oneinstack.com      #
#######################################################################

What Are You Doing?
	1. Use HTTP Only
	2. Use your own SSL Certificate and Key
	3. Use Let's Encrypt to Create SSL Certificate and Key
	q. Exit
Please input the correct option: 2

Please input domain(example: www.example.com): demo.wl52056.top
domain=demo.wl52056.top

Please input the directory for the domain:demo.wl52056.top :
(Default directory: /data/wwwroot/demo.wl52056.top): 
Virtual Host Directory=/data/wwwroot/demo.wl52056.top

Create Virtul Host directory......
set permissions of Virtual Host directory......

Do you want to add more domain name? [y/n]: n

Do you want to redirect all HTTP requests to HTTPS? [y/n]: y

You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.

Country Name (2 letter code) [CN]: 

State or Province Name (full name) [Shanghai]: 

Locality Name (eg, city) [Shanghai]: 

Organization Name (eg, company) [Example Inc.]: 

Organizational Unit Name (eg, section) [IT Dept.]: 

Do you want to add hotlink protection? [y/n]: n

Allow Nginx/Tengine/OpenResty access_log? [y/n]: y
You access log file=/data/wwwlogs/demo.wl52056.top_nginx.log

nginx: [warn] "ssl_stapling" ignored, issuer certificate not found for certificate "/usr/local/nginx/conf/ssl/demo.wl52056.top.crt"
nginx: the configuration file /usr/local/nginx/conf/nginx.conf syntax is ok
nginx: configuration file /usr/local/nginx/conf/nginx.conf test is successful
Reload Nginx......
nginx: [warn] "ssl_stapling" ignored, issuer certificate not found for certificate "/usr/local/nginx/conf/ssl/demo.wl52056.top.crt"
Stoping Tomcat
Using CATALINA_BASE:   /usr/local/tomcat
Using CATALINA_HOME:   /usr/local/tomcat
Using CATALINA_TMPDIR: /usr/local/tomcat/temp
Using JRE_HOME:        /usr/java/jdk1.8.0_141
Using CLASSPATH:       /usr/local/tomcat/bin/bootstrap.jar:/usr/local/tomcat/bin/tomcat-juli.jar
waiting for processes to exit
Starting tomcat
bash: /usr/local/tomcat/bin/startup.sh: Permission denied
Tomcat is not running

#######################################################################
#       OneinStack for CentOS/RadHat 6+ Debian 7+ and Ubuntu 12+      #
#       For more information please visit https://oneinstack.com      #
#######################################################################
Your domain:                  demo.wl52056.top
Nginx Virtualhost conf:       /usr/local/nginx/conf/vhost/demo.wl52056.top.conf
Tomcat Virtualhost conf:      /usr/local/tomcat/conf/vhost/demo.wl52056.top.xml
Directory of:                 /data/wwwroot/demo.wl52056.top
Self-signed SSL Certificate:  /usr/local/nginx/conf/ssl/demo.wl52056.top.crt
SSL Private Key:              /usr/local/nginx/conf/ssl/demo.wl52056.top.key
SSL CSR File:                 /usr/local/nginx/conf/ssl/demo.wl52056.top.csr
[root@izuf63kacqfe8wm1qfu094z oneinstack]# 


```
3. 查看/usr/local/nginx/conf/vhost/demo.wl52056.top.conf和/usr/local/tomcat/conf/vhost/demo.wl52056.top.xml。如果没有自动生成可参考如下：
xml:
```
<Host name="demo.wl52056.top" appBase="/data/wwwroot/demo.wl52056.top" unpackWARs="true" autoDeploy="true">
  <Context path="" docBase="/data/wwwroot/demo.wl52056.top" reloadable="false" crossContext="true"/>
  <Valve className="org.apache.catalina.valves.AccessLogValve" directory="logs"
    prefix="demo.wl52056.top_access_log" suffix=".txt" pattern="%h %l %u %t &quot;%r&quot; %s %b" />
  <Valve className="org.apache.catalina.valves.RemoteIpValve" remoteIpHeader="X-Forwarded-For"
    protocolHeader="X-Forwarded-Proto" protocolHeaderHttpsValue="https"/>
</Host>

```
conf:

```
server {
  listen 80;
  listen 443 ssl http2;
  ssl_certificate /usr/local/nginx/conf/ssl/demo.wl52056.top.crt;
  ssl_certificate_key /usr/local/nginx/conf/ssl/demo.wl52056.top.key;
  ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
  ssl_ciphers EECDH+CHACHA20:EECDH+AES128:RSA+AES128:EECDH+AES256:RSA+AES256:EECDH+3DES:RSA+3DES:!MD5;
  ssl_prefer_server_ciphers on;
  ssl_session_timeout 10m;
  ssl_session_cache builtin:1000 shared:SSL:10m;
  ssl_buffer_size 1400;
  add_header Strict-Transport-Security max-age=15768000;
  ssl_stapling on;
  ssl_stapling_verify on;
  server_name demo.wl52056.top;
  access_log /data/wwwlogs/demo.wl52056.top_nginx.log combined;
  index index.html index.htm index.jsp;
  root /data/wwwroot/demo.wl52056.top;

  #error_page 404 /404.html;
  #error_page 502 /502.html;

  location ~ .*\.(gif|jpg|jpeg|png|bmp|swf|flv|mp4|ico)$ {
    expires 30d;
    access_log off;
  }
  location ~ .*\.(js|css|txt)?$ {
    expires 7d;
    access_log off;
  }
  location ~ /\.ht {
    deny all;
  }
  location ~ {
    proxy_pass http://127.0.0.1:8080;
    include proxy.conf;
  }
}

```
4. 访问demo.wl52056.top 能访问说明配置成功
5. [配置ssl可参考我的另一篇博文](http://blog.wl52056.top/2018/06/29/nginx%20ssl%E9%85%8D%E7%BD%AE(%E5%85%8D%E8%B4%B9ssl%EF%BC%89/)