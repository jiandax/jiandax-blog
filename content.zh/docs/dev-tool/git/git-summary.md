---
title: 概述
description: git
date: 2021-05-28
draft: false
weight: 1
---

# Git
## Git 概述
- Git 是一个开源的**分布式**版本控制工具



### 集中式

#### 记录差异

- **维护增量**
- 将保存的信息看作是一组基本文件和每个文件随时间逐步积累的差异
  <img src="/images/202105/jiandax_20210528205301.png"  width=80% height=80%/>



#### 脆弱的中央库

- 数据不安全：存在单点故障、黑客攻击的问题，需做好数据备份
- 服务器压力大：所有操作都需要与服务器交互，受限于宽带
- 强调集中管理：适合人数不多的项目



### 分布式

#### 记录快照

- **维护全量**
- 把数据看作是对小型文件系统的一组快照
- 每次提交更新，都会对当前的全部文件制作一个快照并保存这个快照的索引。
- 为了高效， 如果文件没有修改，Git 不再重新存储该文件， 而是只保留一个链接指向之前存储的文件。
  <img src="/images/202105/jiandax_20210528205316.png" width=80% height=80%/>



#### 强壮的分布库

- 数据安全完整：所有节点都是服务器，无带宽和性能瓶颈；提交全部使用SHA1哈希
- 效率高：提交为本地操作，全离线操作；编码不会被冲突打断
- 强调个体：适合分布式开发



### 工具选型

- SVN不适合的领域
  - 跨地域的协同开发
  - 追求高质量代码和代码门禁
- Git不适合的领域
  - word等二进制文档的版本控制
  - 目录级别的读授权
  
## Git 安装

### Linux 平台

- 下载源码包：https://git-scm.com/download

- 解压安装下载的源码包

  ```shell
  $ tar -zxf git-1.7.2.2.tar.gz
  $ cd git-1.7.2.2
  $ make prefix=/usr/local all
  $ sudo make prefix=/usr/local install
  ```

  

### Windows 平台

- 下载安装包：https://npm.taobao.org/mirrors/git-for-windows/
- 按提示默认安装即可



## Git 配置

### 配置文件

- 系统级：/etc/gitconfig
- 用户级：[用户目录]/.gitconfig
- 项目级：[项目目录]/.git/config



### 配置信息

```bash
# 配置个人的用户名称和电子邮件地址
$ git config --global user.name "jiandax"
$ git config --global user.email jiandax@163.com

# 配置Git默认使用的文本编辑器
$ git config --global core.editor emacs

# 配置差异分析工具
$ git config --global merge.tool vimdiff

# 查看配置信息
$ git config --list
```