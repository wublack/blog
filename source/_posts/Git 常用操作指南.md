---
title: Git 常用操作指南
date: 2018-04-27 16:40:00
tags: Git
---

# Git 常用操作指南

1. 在我们常常去git 上clone一个项目的时候，会要求用户名和密码，这样输入会比较麻烦，这里给大家介绍一个好的git clone的方法
```git
git clone http://username:userpwd@192.168.1.103:3000/projectname/android-demo.git
```

2. 在我们git pull 或者git push 的时候常常要我们输入密码，每次都要输入，是不是很烦，设置一下吧
```git
git config --global credential.helper store
```


1. 查看提交历史
```git
git log --pretty=oneline --abbrev-commit
```

2. 给历史打tag
```git
git tag v1.0 6224937
```

3. 推送打tag
```git
git push origin v1.0
```


