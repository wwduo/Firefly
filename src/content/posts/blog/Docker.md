---
title: Docker的安装
published: 2026-06-07
description: 本文介绍各系统如何Docker
tags:
  - 前端
  - 开发
category: 测试文本
draft: false
author: xizesha
date: 2026-06-12
---
Docker是基于Linux的容器化技术。在Windows和Mac电脑上，Docker通过虚拟化一个Linux子系统来运行。

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