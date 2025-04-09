---
title: Linux\Shell
weight: 2501
#next: /guide
prev: /guide
#editURL: "https://example.com/edit/this/page"
type: "docs"
toc: true
math: true
---

## good

### test


## 1. Linux 概述
### 1.1. Linux 是什么？

- Linux 是一个开源、免费的操作系统内核，由芬兰程序员 Linus Torvalds 在 1991 年 首次发布。
- 广泛应用于服务器、超级计算机、嵌入式设备（如路由器、智能电视）以及个人电脑（如 Ubuntu、Fedora）。


<br>

### 1.2. Linux 系统目录结构

![1744208543004](1744208543004.png)

```markdown
/		  [根目录，所有目录的起点]
├── bin    [核心命令：存放系统启动和运行必需的基础命令，如 ls/cp/bash]
├── sbin   [管理员命令：存放系统管理命令，如 iptables/reboot，需 root 权限]
├── boot   [启动文件：包含内核(vmlinuz)和引导加载器(GRUB)文件]
├── dev    [设备文件：硬件设备抽象文件，如 /dev/sda(硬盘)、/dev/tty(终端)]
├── etc    [配置文件：系统和应用程序的配置，如 /etc/passwd(用户)、/etc/nginx/]
├── home   [用户目录：普通用户的家目录，如 /home/username 存放个人文件]
├── root   [root家目录：超级用户的家目录，普通用户无权访问]
├── lib    [核心库：存放/bin和/sbin所需的共享库(.so文件)]
├── usr    [用户软件：相当于Windows的Program Files]
│   ├── bin    [非必需的用户命令]
│   ├── sbin   [非必需的管理命令]
│   └── lib    [应用程序库文件]
├── opt    [第三方软件：商业软件或大型应用，如 Oracle/Matlab]
├── proc   [内核/进程信息：虚拟文件系统，实时反映进程和内核状态]
├── sys    [系统设备：虚拟文件系统，管理设备驱动和内核参数]
数据：存放系统启动后的临时文件(如PID文件)]
├── var    [可变数据：经常变化的文件]
│   ├── log    [系统日志：如 /var/log/syslog]
│   └── cache  [应用程序缓存]
├── tmp    [临时文件：所有用户可读写，重启后通常清空]
├── mnt    [手动挂载：临时挂载点(如U盘/硬盘)]
└── media  [自动挂载：可移动设备自动挂载点(如光盘/U盘)]
```

<br>

### 1.3. Linux 文件基本属性:

> [!TIP]
> Linux 系统是一种典型的多用户系统，不同的用户处于不同的地位，拥有不同的权限。

```markdown
文件类型  所有者权限  组权限  其他用户权限
   ↓        ↓        ↓        ↓
   -    r w x      r - -      r - -
        ↑ ↑ ↑      ↑ ↑ ↑      ↑ ↑ ↑
        │ │ └执行  │ │ └执行  │ │ └执行
        │ └─写入   │ └─写入   │ └─写入
        └──读取    └──读取    └──读取
```

1️⃣ **文件类型**：

- `d`（文件\目录）；
- `-`（文本、二进制、压缩包等常规文件）；
- `l`（符号链接，指向另一个文件的快捷方式（软链接））
- ......

2️⃣ **用户身份划分**：

- 所有者（Owner）：文件的创建者/拥有者，拥有最高控制权。
- 所属组（Group）：文件所属的用户组，组内成员共享组权限。
- 其他用户（Others）：既不是所有者也不在所属组的其他用户。

3️⃣ **权限类型**：每种用户身份对应三种基本权限：

- 读 `r`：查看文件内容或列出目录内容。
- 写 `w`：修改文件内容或在目录中创建/删除文件。
- 执行 `x`：运行文件（如脚本）或进入目录。

4️⃣ **权限表示法**：符号模式；数字模式

- ***符号模式：*** 用 `r，w，x` 表示权限；
- ***数字模式：*** 用八进制数表示，***每位数字对应*** `r=4、w=2、x=1` ***的和***；

||符号模式|数字模式|
|:-:|-|-|
|权限案例|`rw-r--r--`|644|
|所有者|`rw-`（读写）|6 = 4+2（读写）|
|所属组|`r--`（只读）|4 = 4（只读）|
|其他用户|`r--`（只读）|4 = 4（只读）|

<br>

### 1.4. Linux 常用命令

|||
|:-:|:-:|
|📂 文件\文件夹权限|`ls`, `chmod`, `chown`, `chgrp`|
|||
|||
|||
|||
|||
|||
|||

<br>

#### 📂 文件\文件夹权限：

1️⃣ **使用 `ls -l` 命令查看文件权限：**

```shell
$ ls -l
-rw-r--r-- 1 alice dev 1024 Sep 1 10:00 file.txt
```
- 第1字段 `-rw-r--r--`：文件类型和权限。
- 第3字段 `alice`：所有者。
- 第4字段 `dev`：所属组。

<br>

2️⃣ **`chmod` 更改权限**

```shell
$ chmod u+x script.sh
$ chmod g-w file.txt
$ chmod 755 script.sh
```
- 给所有者添加执行权限
- 移除所属组的写权限
- 数字模式：rwxr-xr-x

<br>

3️⃣ **`chown` 更改所有者和所属组**

```shell
$ chown alice:dev file.txt  
```
- 修改所有者为 alice，组为 dev

<br>

4️⃣ **`chgrp` 单独修改所属组**

```shell
$ chgrp dev file.txt
```

<br>

#### 🛣 路径查看\切换：




> **：**

👻

<br>

> **：**



<br>


###  文件与目录操作

|命令|作用\实例|
|:-:|-|
|`xx --help`|***查看帮助：***|
|`pwd`|1️⃣ ` $ cd /home`（切换目录）<br> `$ cd ..`（返回上级）|
|`ls`	|1️⃣ `$ ls -l`（列出目录内容）<br> 2️⃣ `$ ls -a`（显示隐藏文件）|
|`chmod`|1️⃣ `$ chmod u+x test.sh`（）<br> 2️⃣ `$ chmod g-w file.txt`（）<br>  `$ chmod 755 test.sh`（）|
|`touch`|***创建空文件或更新时间戳***<br>`$ touch newfile.txt`|



https://www.unicode.org/emoji/charts/full-emoji-list.html

<br>


| 命令    | 作用                     | 示例                                      |
|---------|--------------------------|------------------------------------------|
| `mkdir` | 创建目录                 | `mkdir dir`<br>`mkdir -p dir1/dir2`（递归创建） |
| `rm`    | 删除文件/目录            | `rm file.txt`<br>`rm -r dir/`（递归删除）<br> `rm -f file 或 dir/`（强制删除） |
| `cp`    | 复制文件/目录            | `cp file1.txt file2.txt`<br>`cp -r dir1/ dir2/` |
| `mv`    | 移动/重命名文件          | `mv old.txt new.txt`<br>`mv file /tmp/`   |
| `cat`   | 查看文件内容             | `cat file.txt`                           |
| `grep`  | 文本搜索                 | `grep "error" log.txt`<br>`grep -r "pattern" /dir/` |
| `find`  | 查找文件                 | `find /home -name "*.txt"`               |

<br>

## 🖥️ 系统信息与管理
| 命令         | 作用                     | 示例                                      |
|--------------|--------------------------|------------------------------------------|
| `top`/`htop` | 实时进程监控             | `top`<br>`htop`（需安装）                |
| `ps`         | 查看进程                 | `ps aux` <br> `ps -ef`&#124;`grep nginx` |
| `kill`       | 终止进程                 | `kill -9 1234`（强制终止 PID 1234）      |
| `df`         | 查看磁盘空间             | `df -h`（人类可读格式）                  |
| `du`         | 查看目录大小             | `du -sh /home/`（汇总大小）              |
| `free`       | 查看内存使用             | `free -h`                                |
| `systemctl`  | 管理系统服务             | `systemctl start nginx`<br>`systemctl status sshd` |
| `shutdown`   | 关机/重启                | `shutdown now`<br>`reboot`               |

<br>

## 🌐 网络操作
| 命令       | 作用                     | 示例                                      |
|------------|--------------------------|------------------------------------------|
| `ping`     | 测试网络连通性           | `ping google.com`                        |
| `ifconfig`/`ip` | 查看/配置网络接口    | `ifconfig`<br>`ip addr`                  |
| `curl`/`wget` | 下载文件             | `curl -O http://example.com/file`<br>`wget http://example.com/file` |
| `ssh`      | 远程登录                 | `ssh user@192.168.1.1`                   |
| `scp`      | 远程复制文件             | `scp file.txt user@host:/path/`          |
| `netstat`/`ss` | 查看网络连接/端口    | `netstat -tulnp`<br>`ss -tulnp`          |

<br>

## 👥 用户与权限管理
| 命令      | 作用                     | 示例                                      |
|-----------|--------------------------|------------------------------------------|
| `useradd` | 添加用户                 | `useradd -m newuser`                     |
| `passwd`  | 修改密码                 | `passwd username`                        |
| `sudo`    | 提权执行命令             | `sudo apt update`                        |
| `chmod`   | 修改权限                 | `chmod 755 script.sh`                    |
| `chown`   | 修改文件所有者           | `chown user:group file.txt`              |

<br>

## 📦 软件包管理
| 命令（Debian/Ubuntu） | 命令（RHEL/CentOS） | 作用              | 示例                                      |
|-----------------------|---------------------|-------------------|------------------------------------------|
| `apt update`          | `yum update`        | 更新软件包列表    | `sudo apt update`                        |
| `apt install`         | `yum install`       | 安装软件          | `sudo apt install nginx`                 |
| `apt remove`          | `yum remove`        | 卸载软件          | `sudo apt remove nginx`                  |
| `dpkg -i`             | `rpm -i`           | 安装本地包        | `sudo dpkg -i package.deb`               |

<br>

## 🛠️ 其他实用工具
| 命令       | 作用                     | 示例                                      |
|------------|--------------------------|------------------------------------------|
| `tar`      | 压缩/解压文件            | `tar -czvf archive.tar.gz dir/`<br>`tar -xzvf archive.tar.gz` |
| `crontab`  | 定时任务管理             | `crontab -e`（编辑）<br>`crontab -l`（查看） |
| `history`  | 查看命令历史             | `history \| grep "apt"`                  |
| `alias`    | 设置命令别名             | `alias ll='ls -alF'`                     |

<br>

## 🛠️ 其他命令
|命令|作用|
|-|-|
|||

<br>





<br>

# 参考网址：

- https://www.w3ccoo.com/linux/
- https://www.tutorialspoint.com/unix/unix-getting-started.htm












