---
title: "安装配置"
description: "git-install"
date: 2021-05-26
draft: false
weight: 1
---



# Git 安装

## Linux 平台

- 下载源码包：https://git-scm.com/download

- 解压安装下载的源码包

  ```shell
  $ tar -zxf git-1.7.2.2.tar.gz
  $ cd git-1.7.2.2
  $ make prefix=/usr/local all
  $ sudo make prefix=/usr/local install
  ```

  

## Windows 平台

- 下载安装包：https://npm.taobao.org/mirrors/git-for-windows/
- 按提示默认安装即可



# Git 配置

## 配置文件

- 系统级：/etc/gitconfig
- 用户级：[用户目录]/.gitconfig
- 项目级：[项目目录]/.git/config



## 配置信息

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