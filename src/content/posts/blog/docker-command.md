---
title: Docker常用命令
published: 2026-06-12
description: 这是文章的简短描述
tags:
  - Docker
category: Docker
draft: false
author: xizesha
---
**docker images：列出所有已下载到本地的Docker镜像。

**docker rmi image_name 或 docker rmi image_id**：删除镜像

**docker pull** **--platform=xxx** **nginx：拉取特定CPU架构的镜像

**docker ps  -a：支持查看运行和已停止的容器

docker ps默认只查看运行中的容器

**docker run** **-p** **端口号1:端口号2 镜像名**

- 每个容器运行在独立的虚拟网络环境中，与宿主机的网络隔离，默认无法直接从宿主机访问容器内部网络。
- -p参数将宿主机的端口映射到容器内部的端口。
- -p 宿主机端口:容器内部端口（先外后内）
*  **示例**: `-p 80:80`将宿主机的80端口转发到容器内的80端口。

**docker run** **-v** **宿主机目录:容器内目录 镜像名**

- 功能: 将宿主机的文件目录与容器内的文件目录进行绑定。使得在任一方修改该文件夹时，另一方都会同步修改
- 挂载卷：绑定的目录就称为挂载卷
- 目的: 实现数据的**持久化保存**。当容器被删除时，容器内的数据也会被删除，但**挂载卷可确保容器删除时，数据仍保存在宿主机上**。

**docker volume list：查看所有创建过的卷

**docker volume rm 卷名：删除卷

**docker volume prune -a：删除所有没有任何容器在使用的卷

**docker run -e xxx：传递环境变量，可多次-e

- 可在dockerhub上搜索容器对应镜像，可传递的环境变量有哪些

**docker run** **--***name 容器名：指定容器的名字，该名字在整个宿主机上必须唯一，不能重复

**docker run -it：控制台可以进入容器内部交互，类似于从宿主机进入了容器的cmd

**docker run --rm：当容器停止时，删除容器

- -it 常常和 --rm搭配使用，用于临时调试容器

**docker run --restart xxx：用于配置容器停止时的重启策略

- always：容器停止就立即重启
- unless-stopped：意外停止重启，但手动停止不重启

**docker rm -f 容器ID或容器名**

- 删除容器
- -f：force，强制删除，对正在运行的容器需要加上

**docker stop 容器ID或容器名：停止一个正在运行的容器，停止后，docker ps查询不到该容器

**docker start 容器ID或容器名：重新启动一个已停止的容器。

**docker create：**使用和docker run相同，但只创建容器，不立即启动（回顾：docker run = 创建+启动），如果要启动，用 docker start

**docker logs 容器ID或容器名**：查看容器的命令

**docker exec -it 容器ID /bin/sh**：进入容器内部获得交互式命令行环境，可进行文件系统查看、进程管理或深入调试。