---
title: linux
published: 2026-07-16
description: 这是文章的简短描述
image: ./cover.jpg
tags:
  - 开发
category: 前端开发
draft: true
author: xizesha
---
## 一、Linux 系统桌面常用单词翻译

1. new folder 新建文件夹
2. paste 粘贴
3. select all 全选
4. open in terminal 打开终端 / 命令行
5. keep aligned 保持对齐
6. organize deaktop by name 按名称组织桌面
7. change background 更改背景
8. cancel 取消
9. create 创造 创建
10. wallpapers 壁纸
11. notifications 通知
12. search 搜索
13. region 区域
14. univetsal access 通用存取
15. online accounts 联机帐户
16. privacy 隐私
17. sharing 共享
18. sound 声音
19. power 权力 权限
20. network 网络
21. lock screen 锁频
22. open in new tab 在新标签页中打开
23. open in new window 在新窗口中打开
24. cut 剪切
25. copy 复制
26. move to 移动到
27. copy to 复制到
28. move to trash 移到垃圾箱 删除
29. resize icon 调整图标大小
30. rename 重命名
31. compress 压紧 压缩
32. properties 属性

## 二、学习笔记

### 命令组成结构

命令本体 command + 选项，控制命令的行为细节［-options］+ 参数，控制命令的指向目标［parameter］

1. **ls 命令**，作用是列出目录下的内容，语法如下：`ls[-a-l-h][linux路径]`
    
    - `ls -l -a`、`ls -la`、`ls -al`
    - 三种写法都是一样的，同时应用 - l (竖向排列展示内容) 和 - a（列出所有文件夹，包含隐藏的）功能
    
2. **cd 命令** 切换工作目录
    
    - 语法：`cd+［linux路径］`参数
    
3. **pwd** 查看当前工作目录
    
    - 语法：`pwd`
    
4. 路径区分
    
    （1）绝对路径：以根目录为起点，路径描述以`/`开头
    
    - 写法：`cd /home/ittangmao/Desktop`
        
        （2）相对路径：以当前目录为起点 路径描述无需以`/`开头
    - 写法：`cd Desktop`
    
5. **mkdir**命令，创建新目录（文件夹）
    
    - 语法：`mkdir [-p] Linux路径`（参数必须填写）
    
6. **touch**命令创建文件
    
    - 语法：`touch ［Linux］路径`
    
7. **cat**查看文件内容
    
    - 语法：`cat linux路径`
    
8. **more** 查看文件内容 可以翻页查看（按空格翻页 按 q 退出查看）
    
    - 语法：`more linux路径`
    
9. **cp** 复制文件或者文件夹
    
    - 语法:
        
        （1）复制文件 `cp 参数1（复制的文件内容） 参数2（复制去的地方）`
        
        （2）复制文件夹 `cp -r 参数1 参数2`
    
10. **mv** 移动文件或者文件夹
    
    - 语法：`mv (-r) 参数1 参数2`
    
11. **rm**删除文件 文件夹
    
    - 语法:`rm [-r -f] 参数1 参数2 …参数N`
    - `-r` 用于删除文件夹
    - `-f` 用于强制删除
    
12. 用户切换
    
    - `su - root` 输入密码 123456（默认的），临时切换到 root 用户
    - `exit` 切换回普通用户
    
13. 用户组管理（需要 root 权限）
    
    - `groupadd 用户名`（创建用户组）
    - `groupdel 用户名`（删除用户组）
    
14. `getent group` 查看当前系统有多少用户组
    
15. 认知权限信息：
    
    - `r (read)`查看权限
    - `w (write)`修改权限
    - `x (execute)`执行权限
    
16. **chmod** 命令 修改文件、文件夹 的权限信息（只有文件，文件夹 所属用户或者 root 用户可以修改）
    
    - 语法：`chmod ［-R］权限 文件或文件夹`
    - 例：`chmod u＝rwx，g＝rx，o＝x hello.txt`（将文件权限改为：rwxr-x--x）
    - 例：`chmod -R u＝rwx，g＝rx，o＝x test`(将文件夹 test 以及内容全部权限设置为 rwxr-x---x)
    
17. 权限数字表示
    
    - r 记为 4，w 记为 2，x 记为 1
    - 0: 无任何权限，即 `---`
    - 1: 仅有 x 权限，`--x`
    - 2：仅有 w 权限，`-w-`
    - 3: 有 w 和 x 权限，`-wx`
    - 4: 仅有 r 权限，`r--`
    - 5: 有 r 和 x 权限，`r-x`
    - 6: 有 r 和 w 权限，`rw-`
    - 7: 有全部权限：`rwx`
    - 示例：751 表示`rwx`（7）`r-x`(5) `--x`(1)
    
18. **chown**命令 修改文件、文件夹的所属用户和用户组 ，只适用 root 用户执行
    
    - 语法：`chown [-R] ［用户］［：］［用户组］文件或文件夹`
    - `-R`：对文件夹全部内容应用相同规则
    - `：`：用于分隔用户和用户组
    - 示例：
        
        1. `chown root hellow.txt`(将 hello.txt 所属用户修改为 root)
        2. `chown :root hellow.txt`(将 hellow.txt 所属用户组修改成 root)
        3. `chown root:ittangmao hellow.txt`(将 hellow.txt 所属用户修改为 root，用户组修改为 ittangamao）
        4. `chown -R root test` (将文件夹 test 所属用户修改为 root 并对文件夹内全部内容应用同样规则
        
    - 总结：无`:` 只改所属用户；`:`右边有名称，改用户组；左右都有内容，用户、用户组都改
    
19. Linux 快捷键：
    
    - `ctrl+c` 强制停止程序，退出命令输入
    - `ctrl+d` 退出或登出（不能用于 vi/vim）
    - `history` 查看历史命令
    - `history ｜grep ch`（在历史记录中过滤带有 ch 命令）
    - `！+命令的前缀`，自动匹配上一次匹配的前缀命令
    - `ctrl+r` 输入内容去匹配历史命令
    
    光标移动快捷键：
    
    - `ctrl+a` 调到命令开头
    - `ctrl+e` 跳到命令结尾
    - `ctrl+键盘左键`，向左跳一个单词
    - `ctrl+键盘右键`，向右跳一个单词
    - `ctrl+l`或者`clear` 清空终端内容（清屏）
    
20. **yum**命令 RPM（安装包）软件管理器，用于自动化安装配置 Linux 软件
    
    - 语法：`yum [-y] ［install ｜remove ｜search］软件名称`
    - `-y`：自动确认，无需手动确认安装 卸载
    - `install`安装、`remove`卸载、`search`搜索
    - 备注：yum 命令需要 root 权限，需联网
    
21. **systemctl**命令控制服务：启动、停止、开机自启，能够被 systemctl 管理的软件，一般也称之为服务
    
    - 语法：`systemctl start ｜ stop｜ status ｜enable ｜disable 服务名`
    - 对应操作：启动 / 停止 / 查看状态 / 开启开机自启 / 关闭开机自启
    
22. 常见系统服务
    
    - NetworkManager 主网络服务
    - network 副网络
    - firewalld 防火墙
    - sshd，ssh 服务（FinalShell 远程连接 Linux 使用的就是这个服务）
    
23. **ln**命令 创建软连接（类似 windows 系统的快捷方式）
    
    - 语法：`ln -s 参数1 参数2`
    - `-s` 创建软连接
    - 参数 1：被链接的文件或文件夹
    - 参数 2：要链接去的目的地
    - 示例：
        
        - `ln -s /etc/yum.conf ～/yum.conf`
        - `ln -s /etc/yum ～/yum`
        
    
24. **date**命令 查看系统的时间
    
    - 语法：`date [-d] [+格式化字符串]`
    - `-d`：按照给定的字符串显示日期，一般用于日期计算
    - 格式字符串：
        
        - `%Y` 年；`%y`年份的后两位数（00..99）
        - `%m`月份（01..12）；`%d`日（01..31）
        - `%H`小时（00..23）
        - `%M`分钟（00..59）
        - `%S`秒（00..60）
        - `%s` 自 1970-01-01 00∶00∶00 UTC 到现在的秒数
        
    
25. 修改时区步骤：
    
    1. 先切换 root 权限
    2. `rm -f /etc/localtime` （删除本地时间）
    3. `ln -s /usr/share/zoneinfo/Asia/shanghai /etc/localtime` (将上海时区文件链接为本地时间)
    4. `ntpdate -u ntp.aliyun.com`(阿里云 ntp 服务器实时校准系统时间，需 root 权限)
    
26. 特殊 IP 地址
    
    - `127.0.0.1` 指代本机
    - `0.0.0.0` 特殊 ip 地址
        
        1. 可用于指代本机
        2. 在端口绑定中用来确定绑定关系
        3. 在 ip 地址限制中 表示所有 ip
        
    
27. 主机名操作
    
    - `hostname` 查看主机名字
    - `hostnamectl set-hostname 新名字`（更改主机名字，需要 root）
    
28. DHCP 与固定 IP 配置
    
    - DHCP：动态获取 ip 地址，每次重启都重新获取一次
        
    - 配置固定 ip 地址步骤：
        
        ①在 VMware 中（或 Fusion）中配置 ip 地址网关和网段（ip 地址范围）
        
        子网设置为：`192.168.88.0`
        
        子网掩网为：`255.255.255.0`
        
        NAT 设置：网关：`192.168.88.2`
        
        ②在 linux 系统中手动修改配置文件，固定 ip
        
        bash
        
        运行
        
        ```
        su - root
        vim /etc/sysconfig/network-scripts/ifcfg-ens33
        ```
        
        将`BOOTPROTO="dhcp"`改为`BOOTPROTO="static"`
        
        新增配置：
        
        plaintext
        
        ```
        IPADDR="192.168.88.130"
        NETMASK="255.255.255.0"
        GATEWAY="192.168.88.2"
        DNS1=192.168.88.2
        ```
        
    
29. ping 连通性检测
    
    - 语法:`ping [-c num] ip或主机名`
    - 选项:`-c`, 检查的次数，不使用`-c`选项，将无限次数持续检查
    - 参数:ip 或主机名，被检查的服务器的 ip 地址或主机名地址
    
30. wget 命令行下载网络文件
    
    - 语法:`wget [-b] url`
    - 选项:`-b`, 可选，后台下载，会将日志写入到当前工作目录的 wget-log 文件
    - 参数: url, 下载链接
    - 例 1: 下载 hadoop 安装包
    
    bash
    
    运行
    
    ```
    wget http://archive.apache.org/dist/hadoop/common/hadoop-3.3.0/hadoop-3.3.0.tar.gz
    ```
    
    - 例 2：后台下载
    
    bash
    
    运行
    
    ```
    wget -b http://archive.apache.org/dist/hadoop/common/hadoop-3.3.0/hadoop-3.3.0.tar.gz
    ```
    
31. curl 发送 http 网络请求，可下载文件、获取信息
    
    - 语法: `curl ［-o］url`
    - 选项:`-o`, 用于下载文件，url 是下载链接时，使用此选项保存文件
    - 参数: url, 要发起请求的网络地址
    
32. 端口分类
    
    - 物理端口：可见端口，如 usb 接口，rj45 网口，hdmi 端口
    - 虚拟端口：计算机内部的端口，用于操作系统和外部交互
    - ip 锁定计算机，端口锁定具体软件
        
        ①公认端口：1~1023, 系统 / 知名程序预留，如 SSH 22 端口、HTTPS 443 端口，非特殊需求不要占用
        
        ②注册端口：1024~49151，可自由绑定程序 / 服务
        
        ③动态端口：49152~65535，程序对外连接时临时使用
    
33. 进程管理
    
    - `ps`查看 Linux 系统进程信息
    - 语法:`ps [-e -f]`
        
        - `-e`：显示全部进程
        - `-f`：完整格式化展示全部信息
        
    - 过滤进程：`ps -ef ｜grep 关键字`
    - 固定用法：`ps -ef` 列出全部进程完整信息
    - 关闭进程：`kill［-9］进程id`
        
        - `-9`：强制关闭；不加仅发送关闭信号，进程可拒绝关闭
        
    
34. top 查看 CPU、内存使用情况（类似 Windows 任务管理器，默认 5 秒刷新一次）
    
    - 语法:`top`
    - 按`q`或`ctrl+c`退出
    
35. df 查看硬盘信息
    
    - 语法：`df [-h]`
    - `-h`：人性化单位展示容量
    
36. iostat 查看 CPU、磁盘相关信息
    
    - 语法:`iostat [-x] [num1][num2]`
    - `-x`：显示更多信息
    - num1：刷新间隔；num2：刷新次数
    
37. sar 网络统计
    
    - 语法: `sar -n DEV num1 num2`
    - `-n`：查看网络，DEV 代表网络接口
    - num1：刷新间隔（不填只查看一次）
    - num2：查看次数（不填无限次数）
    
38. 环境变量
    
    - 定义：操作系统运行时记录的关键信息，辅助系统运行，Key-Value 键值对结构
    - 查看环境变量：`env`
    
39. 自定义环境变量
    
    1. 临时设置：`export 变量名=变量值`
    2. 永久生效
        
        ①仅当前用户：配置文件 `~/.bashrc`
        
        ②所有用户：系统配置文件 `/etc/profile`
        
        ③生效命令：`source 配置文件`，或重新登录终端生效
    
40. rz sz 文件上传下载
    
    - 安装命令：`yum -y install lrzsz`
    - 上传：`rz`
    - 下载：`sz 要下载的文件`
    - 文件自动下载到桌面的 fadownload 文件夹内
    
41. 压缩与解压
    
    Linux/Mac 常用两种压缩格式：
    
    ①tar：归档文件，仅封装文件，不压缩体积
    
    ②tar.gz：gzip 压缩格式，大幅减小文件体积
    
    tar 命令语法：`tar[-c -v -x -f -z -C] 参数1参数2 ... 参数N`
    
    - `-c`：创建压缩包，压缩模式
    - `-v`：展示压缩 / 解压进度
    - `-x`：解压模式
    - `-f`：指定压缩包文件，必须放在所有选项最后
    - `-z`：gzip 压缩模式，不加则为普通 tar 包
    - `-C`：指定解压目录，仅解压使用
    
    tar 压缩示例：
    
    1. 普通 tar 包：`tar -cvf test.tar 1.txt 2.txt 3.txt`
    2. gzip 压缩包：`tar -zcvf test.tar.gz 1.txt 2.txt 3.txt`
    
    > 注意：`-z`放选项最前，`-f`放选项最后
    
    tar 解压示例：
    
    1. 解压到当前目录：`tar -xvf test.tar`
    2. 解压到指定目录：`tar -xvf test.tar -C /home/itheima`
    3. gzip 包解压到指定目录：`tar -zxvf test.tar.gz -C /home/itheima`
    
    > 注意：`-f`必须在选项末尾，`-z`建议开头，`-C`单独书写
    
    zip 压缩命令：
    
    - 语法: `zip [-r] 参数1参数2...参数N`
    - `-r`：压缩包含文件夹时使用，递归处理目录
    - 示例：
        
        bash
        
        运行
        
        ```
        zip test.zip a.txt b.txt c.txt
        zip -r test.zip test itheima a.txt
        ```
        
    
    unzip 解压命令：
    
    - 语法: `unzip [-d] 参数`
    - `-d`：指定解压目录，等价 tar 的 - C
    - 参数：待解压 zip 压缩包文件