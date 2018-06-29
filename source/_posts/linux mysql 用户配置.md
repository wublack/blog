---
title: linux mysql 用户配置
date: 2018-06-29 11:09:22
tags: linux mysql
---

# linux mysql配置

1. [安装MySQL数据库](https://www.cnblogs.com/bookwed/p/5896619.html)请参考该网站。
2. 执行mysql -u username -p #username为用户名
```
mysql -u root -p
```
3. 进入mysql，show databases;
查看所有的数据库。create database db_name 创建自己数据库
实例如下：
```
#查看
$ show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
| wl_db              |
+--------------------+
5 rows in set (0.00 sec)

#创建
$ create database db_name;
Query OK, 1 row affected (0.00 sec)

```

4. 添加用户
实例如下：
```
#添加只读用户
GRANT SELECT ON *.* TO 'wl_read'@'%' IDENTIFIED BY "wlread";

#撤销添加
revoke SELECT ON *.*  from 'readonly'@'%';

#添加外网可读可写用户
GRANT all privileges ON *.* TO 'db_user'@'%' IDENTIFIED BY "wl123@";

#记得添加防火墙开放端口
firewall-cmd  --zone=public --add-port=3306/tcp --permanent
```

基本操作先到这里，后续有什么问题，继续补充