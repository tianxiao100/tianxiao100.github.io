---
layout:     post
title:      CentOS安装Docker
subtitle:   CentOS安装Docker 全记录
date:       2019-01-25
author:     wangzukun
header-img: img/post-bg-cook.jpg
catalog: true
tags:
    - Docker
    - CentOS
---

参考链接：https://blog.csdn.net/u010046908/article/details/79553227

Docker 要求 CentOS 系统的内核版本高于 3.10 ，查看本页面的前提条件来验证你的CentOS 版本是否支持 Docker 。通过 uname -r 命令查看你当前的内核版本


```
[root@iZj6cd10hr1jugiwclsza6Z ~]# uname -r 
3.10.0-693.2.2.el7.x86_64
```

## 初步安装和启动docker


```
[root@iZj6cd10hr1jugiwclsza6Z ~]# yum -y update
[root@iZj6cd10hr1jugiwclsza6Z ~]# yum -y install docker
[root@iZj6cd10hr1jugiwclsza6Z ~]# systemctl start docker
```
## 设置镜像

阿里云提供“镜像加速器”，地址：
https://xfjnb7ys.mirror.aliyuncs.com

```
[root@iZj6cd10hr1jugiwclsza6Z ~]# vi /etc/docker/daemon.json 

# 文件输入以下内容：
{
  "registry-mirrors": ["https://xfjnb7ys.mirror.aliyuncs.com"]
}
```
## 重启docker

```
[root@iZj6cd10hr1jugiwclsza6Z systemd]# systemctl daemon-reload
[root@iZj6cd10hr1jugiwclsza6Z systemd]# systemctl restart docker.service
```

测试Docker是否正常运行

```
[root@iZj6cd10hr1jugiwclsza6Z systemd]# docker run hello-world

# 结果如下：
Hello from Docker!
This message shows that your installation appears to be working correctly.
```

## 常用命令

```

# 查看镜像
[root@iZj6cd10hr1jugiwclsza6Z systemd]# docker images

# 搜索镜像
[root@iZj6cd10hr1jugiwclsza6Z systemd]# docker search shadowsocks

# 
```