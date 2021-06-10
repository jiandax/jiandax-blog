---
title: 基本命令
description: git-command
date: 2021-05-28
draft: false
weight: 2
---

# 基本命令
## 工程区域
- 工作区：日常工作的工程目录
- 暂存区：又称索引，工程根目录.git/index 文件夹
- 版本区：又称本地仓库，工程根目录.git文件夹
  <img src="/images/202106/jiandax_20210602201101.png"  width=80% height=80%/>



## 基本操作 

### 创建仓库

- **git init**

```bash
# 初始化本地库
# git init [dir]
$ git init
```

- **git clone**

```bash
# 从现有库中拷贝项目
# git clone <repository> <dir>
$ git clone git://github.com/schacon/grit.git myDir
```



### 变更修改

- **git add**

```bash
# 添加文件/文件夹到暂存区
# git add [file1] [file2] ...
$ git add README hello.php

# 格式：git add [dir]
$ git add .
```
- **git rm**

```bash
# 删除工作区和暂存区的文件
# git rm <file>
$ git rm runoob.txt

# 选项：-f 强制删除
$ git rm -f runoob.txt 

# 选项：--cached 仅从暂存区域移除，仍保留在工作区中
$ git rm --cached runoob.txt

# 选项：-r 递归删除
$ git rm –r *
```
- **git mv**

```bash
# 移动或重命名一个文件
# git mv [file] [newfile]
$ git mv test.log test.txt

# 选项：-f 强制
$ git mv -f README README.md
```

- **git commit**

```bash
# 提交暂存区到本地仓库
# git commit -m [message]
$ git commit -m '第一次版本提交' 

# 选项：-m 提交时添加注释信息
# 选项：-a 提交跟踪过的文件
$ git commit -am '第一次版本提交' 

# 选项：--amend 追加提交（修改最近一次的提交）
$ git commit --amend
```



### 回退版本

- **git reset**
```bash
# 格式：git reset [--soft | --mixed | --hard] [HEAD]
# 选项：--soft  在本地库移动 HEAD 指针
# 选项：--mixed 在本地库移动 HEAD 指针、重置暂存区
# 选项：--hard  在本地库移动 HEAD 指针、重置暂存区、重置工作区

$ git reset HEAD^            # 回退所有内容到上一个版本  
$ git reset HEAD^ hello.php  # 回退 hello.php 文件的版本到上一个版本  
$ git reset 052e             # 回退到指定版本

# 后退 n 个版本
$ git reset --hard HEAD^^     # n 为 ^ 的个数
$ git reset --hard HEAD~2     # n 为 ~ 后的数字

```



## 远程操作

- **git remote**
```bash
# 查看远程库
$ git remote -v              # 显示所有
$ git remote show [remote]   # 显示某个

# 新增远程库
# git remote add [库别名] [远程地址]
$ git remote add origin https://github.com/jianda-int/furesky-cms.git

# 删除远程库
# git remote add [库别名] [远程地址]
$ git remote add origin https://github.com/jianda-int/furesky-cms.git
```
- **git fetch、git merge**
```bash
# 拉取远程代码
# git fetch [库别名] [分支名]
$ git fetch origin

# 合并到工作区
# git merge [库别名 / 分支名]
$ git merge origin/master
```

- **git pull**
```bash
# 拉取远程代码并合并
# git pull <远程主机名> <远程分支名>:<本地分支名>
$ git pull origin master                       # 合并到当前分支
$ git pull origin master:brantest              # 合并到brantest分支
```
- **git push**
```bash
# 推送到远程并合并
# git push <远程主机名> <本地分支名>:<远程分支名>
$ git push origin master                       # 合并到master分支
$ git push origin master:brantest              # 合并到brantest分支

# 选项：--force 强制推送
$ git push --force origin master
```



## 分支操作
- **git branch**
```bash
# 查看分支
$ git branch -v

# 创建分支
$ git branch mybranch

# 删除分支
$ git branch -d mybranch
```
- **git checkout**
```bash
# 切换分支
$ git checkout mybranch

# 创建并切换分支
$ git checkout -b mybranch
```
- **git merge**
```bash
# 合并分支
$ git merge mybranch
```



## 查看操作

### 查看差异

- **git status**
```bash
# 查看仓库当前的状态，显示有变更的文件
$ git status

# 选项：-s 精简显示
$ git status -s
```
- **git diff**
```bash
# 对比暂存区和工作区的差异
$ git diff [file]

# 对比暂存区和最后一次提交(HEAD)的差异
$ git diff --cached [file]

# 对比工作区/暂存区和最后一次提交(HEAD)的差异（~X: 表示前第X个版本）
$ git diff HEAD
$ git diff HEAD~X

# 比较两个分支上最后提交的内容的差别
$ git diff <分支名1> <分支名2> 

# 选项：--stat 精简显示
$ git diff --stat
```



### 查看日志

- **git log**
```bash
# 查看历史提交记录
$ git log

# 选项：--oneline 精简显示
$ git log --oneline

# 选项：--reverse 逆向显示
$ git log --reverse

```
- **git blame**
```bash
# 查看指定文件的提交记录
# git blame <file>
$ git blame README.txt 
```



### 查看命令

- **git help**
```bash
# 在网页中，查看帮助文档
$ git help <command>
$ git <command> --help
```


