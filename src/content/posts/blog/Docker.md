---
title: Docker的安装
published: 2026-06-07
description: 本文介绍各系统如何Docker
tags:
  - Docker
category: Docker
draft: false
author: xizesha
date: 2026-06-12
---
核心概念

Docker是一种软件部署技术，利用容器化技术为应用程序封装独立的运行环境。每个运行环境即为一个**容器**，承载容器运行的计算机称为**宿主机**。

容器与虚拟机的区别：

- Docker容器: 多个容器共享同一个系统内核。
- 虚拟机: 每个虚拟机包含一个操作系统的完整内核。
-   优势: Docker容器比虚拟机更轻量、占用空间更小、启动速度更快。

**镜像** (Image)是容器的模板，可类比为软件安装包。镜像类似于制作糕点的模具，可用于创建多个糕点（容器），并可分享给他人。

- 容器是基于镜像运行的应用程序实例，可类比为安装好的软件。

**Docker仓库** (Registry): 用于存放和分享Docker镜像的场所。

-   Docker Hub: Docker的官方公共仓库，存储了大量用户分享的Docker镜像。

Docker是基于Linux的容器化技术。在Windows和Mac电脑上，Docker通过虚拟化一个Linux子系统来运行。

**Docker技术原理简述**

利用Linux内核的两大原生功能实现容器化

- Cgroups (Control Groups): 用于限制和隔离进程的资源使用（为每个容器设置CPU、内存、网络带宽等），确保容器资源消耗不影响宿主机或其他容器。
- Namespaces: 用于隔离进程的资源视图，使得容器只能看到自己内部的进程ID、网络资源和文件目录，而看不到宿主机的。
- 本质: Docker容器本质上是一个特殊的进程，但进入容器内部后，其表现看起来像一个独立的操作系统。每个docker容器都是一个独立的运行环境，每个容器内部表现的都像一个独立的Linux系统

Linux系统宿主机是最佳的Docker实战环境。

- **Linux系统安装**

  1. 访问`getdocker.com`获取安装脚本。

  2. 执行安装脚本（例如，通过`curl -fsSL https://get.docker.com -o get-docker.sh`下载脚本，然后执行`sudo sh get-docker.sh`）。

  3. 安装完成后，若非`root`用户，需在所有`docker`命令前添加`sudo`以获取管理员权限。

- **Windows系统安装**

  1. 启用Windows功能: 勾选“Virtual Machine Platform”（虚拟机平台）和“适用于Linux的Windows子系统”（WSL）。

  2. 重启电脑: 根据提示完成重启。

  3. 安装WSL:

    *  以管理员身份打开命令提示符（CMD）。

    *  执行`wsl --set-default-version 2`将WSL默认版本设为2。

    *  执行`wsl --update`安装WSL（国内网络建议添加`--web-download`参数减少下载失败）。

  4. 下载并安装Docker Desktop: 从官方网站下载对应CPU架构的安装包（Windows通常为AMD64），按提示完成安装。

  5. 启动Docker Desktop: 需保持Docker Desktop软件运行。

  6. 验证安装: 在Windows终端输入`docker --version`，若能打印版本号则表示安装成功。

- **Mac系统安装**

  1. 根据Mac电脑的芯片类型（Intel或Apple Silicon）下载对应的Docker Desktop安装包。

  2. 按提示完成安装。

命令行使用: 尽管Docker Desktop提供可视化界面，但命令行在各操作系统上通用性更强，因此教程主要通过命令行讲解。