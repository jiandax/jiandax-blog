---
title: "Markdown"
date: 2021-01-12T00:25:51+08:00
description: Test description
draft: false
enableToc: true
---

# 简介

* 是一种可以使用普通文本编辑器编写的 **标记语言**

* 通过简单的标记语法，它可以使普通文本内容具有一定的格式



# 标题

- 语法
  ```html
  # h1
  ## h2
  ### h3
  #### h4
  ##### h5
  ###### h6
  ```

  

# 文字

- 语法

  ```html
  *斜体*
  **粗体**
  ***斜体粗体***
  ~~删除线~~
  ```

- 效果

  *斜体* 
  **粗体**
  ***斜体粗体***
  ~~删除线~~





# 图片

- 语法

  ```html
  ![百度](https://www.baidu.com/img/baidu_jgylogo3.gif "百度一下")
  ```

- 效果

  ![](https://www.baidu.com/img/baidu_jgylogo3.gif "百度一下")



# 链接

- 语法

  ```html
  //超链接
  [百度](http://baidu.com "百度一下")
  
  //自动链接
  <address@example.com>
  
  //页内超链接
  设锚点：<a id="link">目标位置</a>
  跳转到：[锚点](#link)
  ```

- 效果

  [百度](http://baidu.com "百度一下")
  <address@example.com>
  设锚点：<a id="link">目标位置</a>
  跳转到：<a href="#link">锚点</a>



# 列表

- 语法

  ```html
  //无序列表
  - item
  
  //有序列表
  1. item
  ```

- 效果

  - item

  1. item



# 表格

- 语法

  ```html
  左对齐|居中|右对齐
  -|:-:|-:
  1|2|3
  a|b|c
  ```

- 效果

  | 左对齐 | 居中 | 右对齐 |
  | ------ | :--: | -----: |
  | 1      |  2   |      3 |
  | a      |  b   |      c |



# 代码

- 语法

  ```html
  `单行代码`
  
  ​```javascript
  // 多行代码
  function fun(){
  	echo "Hello World!";
  }
  ​```
  ```


- 效果

  `单行代码`

  ```javascript
  // 多行代码
  function fun(){
  	echo "Hello World!";
  }
  ```



# 分割线

- 语法

  ```html
  ---
  ```

- 效果

  ---



#  引用

- 语法

  ```html
  > 一级引用内容
  >> 二级引用内容
  >>> 三级引用内容
  ......
  ```

- 效果

  > 一级引用内容
  > > 二级引用内容
  > >
  > > > 三级引用内容




