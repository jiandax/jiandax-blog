---
title: "实战运用"
description: "git-operate"
date: 2021-05-28T20:43:00+08:00
draft: false
weight: 3
---

# GitHub

## 免密提交

- 生成 SSH Key 文件

  ```bash
  $ ssh-keygen -t rsa -C "youremail@example.com"
  ```

- 打开 ~/.ssh/id_rsa.pub，复制里面的 key

- 回到 github 上，进入Settings，选择 SSH and GPG keys，点击 New SSH key，设置标题，粘贴 key
  
- 验证
  ```bash
  $ ssh -T git@github.com
  Hi origin! You've successfully authenticated, but GitHub does not provide shell access.
  ```



# TortoiseGit

## 与 GitHub 共用密码

- 现象：TortoiseGit 不能共用ssh-keygen产生的密钥

- 原因：TortoiseGit 使用扩展名为ppk的密钥，而不是ssh-keygen生成的rsa密钥

- 方式一：安装 TortoiseGit 安装过程中，选择使用OpenSSH方式
- 方式二：设置 TortoiseGit 网络的ssh客户端位置为 Git\usr\bin\ssh.exe
  <img src="/images/202106/jiandax_20210602230025.png"  width=80% height=80%/>

    

