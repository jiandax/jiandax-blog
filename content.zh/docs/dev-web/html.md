---
title: "HTML"
date: 2021-01-21T00:57:14+08:00
description: 
enableToc: true
draft: false
weight: 1
---



# HTML 简介

## 前言

- 软件架构
  - C/S，客户端/服务器、
  - B/S，浏览器/服务器

- 网页结构
  - 结构：HTML，描述页面的结构  
  - 表现：CSS，控制页面中元素的样式  
  - 行为：JavaScript，响应用户操作 



## HTML

- **超文本标记语言**，Hyper Text Markup Language
- 是一种描述网页的语言，由标签组成
- 不需编译，直接由浏览器执行
- HTML 不区分大小写

| HTML | 描述                                                         |
| :--: | ------------------------------------------------------------ |
| 声明 | \<!DOCTYPE html>,必须放在HTML文档第一行                      |
| 标签 | - 由尖括号包围关键词，比如：\<html><br/> 通常是成对出现，比如：\<p>\</p><br/> 单标签，比如：\<br/> |
| 元素 | 从 开始标签 到 结束标签 的所有代码                           |
| 属性 | 在开始标签中规定，以名称/值对的形式出现                      |
| 注释 | \<!-- 注释内容 -->                                           |

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">         
        <title>标题</title>
    </head>
    <body>
        网页正文
    </body>
</html>
```



# HTML 标签


## 基本结构

### \<html>\<head>\<body>

| 标签       | 描述             |
| ---------- | ---------------- |
| \<html>  | 定义 HTML 文档   |
| \<head>  | 定义网页的头部   |
| \<body>  | 定义网页的主体   |
| \<meta>  | 定义网页的元数据 |
| \<title> | 定义网页的标题   |

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>标题</title>
	</head>
	<body>
		<p>Hello world!</p>
	</body>
</html>
```



## 网页头部

### \<title>\<meta>\<base>

| 标签     | 描述                           |
| -------- | ------------------------------ |
| \<title> | 定义网页的标题                 |
| \<meta>  | 定义网页的元数据               |
| \<base>  | 定义页面链接标签的默认链接地址 |



### \<link>\<script>\<style>

| 标签      | 描述         |
| --------- | ------------ |
| \<link>   | 定义外部资源 |
| \<script> | 定义脚本文件 |
| \<style>  | 定义样式文件 |



## 基本标签

### \<h1>\<p>

| 标签              | 描述            |
| ----------------- | --------------- |
| \<h1> ~ \<h6> | 定义标题，1~6级 |
| \<p>            | 定义段落        |



### \<br>\<hr>

| 标签         | 描述            |
| ------------ | --------------- |
| \<br />      | 定义换行        |
| \<hr />      | 定义水平线      |



## 文本格式化

### \<b>\<i>\<big>\<small>

| 标签     | 描述         |
| -------- | ------------ |
| \<b>     | 定义粗体文本 |
| \<i>     | 定义斜体字   |
| \<big>   | 定义大号字   |
| \<small> | 定义小号字   |



### \<sub>\<sup>\<ins>\<del>

| 标签   | 描述       |
| ------ | ---------- |
| \<sub> | 定义下标字 |
| \<sup> | 定义上标字 |
| \<ins> | 定义插入字 |
| \<del> | 定义删除字 |



### \<code>\<pre>

| 标签  | 描述       |
| ----- | ---------- |
| \<code> | 定义计算机代码 |
| \<pre> | 定义预格式文本 |



## 链接、图片

### URL

```html
//.     代表当前网页所在目录，可省略
//..	代表当前网页所在目录的上一级目录

//绝对路径
<img src="D:/html/img.jpg" />

//相对路径
<img src="../img.jpg" />
```



### \<a>

| 属性     | 描述         |
| -------- | ------------ |
| id、name | 链接名称 |
| title    | 链接提示文字 |
| href     | 链接地址|
| target   | 在何处打开链接：\_blank、\_parent、\_self、\_top |

```html
//链接到资源
<a href="https://www.baidu.com/" />
<a href="../xxx.html" />
<a href="../xxx.rar" />
    
//链接到邮件
<a href="mailto:xxx@qq.com" />

//定义锚点
<a name="mark" />

//链接到锚点
<a href="#mark" />
<a href="../xxx.html#>mark" />
```



### \<img>

| 属性   | 描述               |
| ------ | ------------------ |
| src    | 定义图像的URL      |
| alt    | 定义图像的替代文本 |
| width  | 定义图像的宽       |
| height | 定义图像的高       |

```html
<img src="xxx.jpg" alt="xxx" width="40" height="40" />
```




##  列表

### \<ol>\<ul>\<li>

| 标签  | 描述         |
| ----- | ------------ |
| \<ul> | 定义无序列表 |
| \<ol> | 定义有序列表 |
| \<li> | 定义列表项   |

```html
//无序列表
<ul>
    <li>项目</li>
    <li>项目</li>
</ul>

//有序列表
<ol>
    <li>第一项</li>
    <li>第二项</li>
</ol>
```



### \<dl>\<dt>\<dd>

| 标签  | 描述                 |
| ----- | -------------------- |
| \<dl> | 定义自定义列表       |
| \<dt> | 定义自定义列表项     |
| \<dd> | 定义自定列表项的描述 |

```html
<dl>
	<dt>项目 1</dt>
		<dd>描述项目 1</dd>
	<dt>项目 2</dt>
		<dd>描述项目 2</dd>
</dl>
```



## 表格

### \<table>\<caption>
### \<th>\<tr>\<td>

| 标签  | 描述       | 属性                                        |
| ----- | ---------- | ------------------------------------------- |
| \<table>   | 定义表格     | border：表格边框的宽度 |
| \<caption> | 定义表格标题 |                        |
| \<th> | 定义表头   |                                             |
| \<tr> | 定义行     |                                             |
| \<td> | 定义单元格 | colspan：横跨的列数<br/>rowspan：横跨的行数 |

```html
<table border="1" width="70%" cellspacing="0">
    <caption>表格标题</caption> 
    <tr>
        <th>北京</th>
        <th>上海</th>
        <th>广州</th>
    </tr>
    <tr>
        <td>...</td>
        <td>...</td>
        <td>...</td>
    </tr>
</table>
```



### \<thead>\<tbody>\<tfoot>

| 标签     | 描述           |
| -------- | -------------- |
| \<thead> | 定义表格的页眉 |
| \<tbody> | 定义表格的主体 |
| \<tfoot> | 定义表格的页脚 |



## 表单

### \<form>

| 属性           | 描述                       |                                                              |
| -------------- | -------------------------- | ------------------------------------------------------------ |
| name           | 名称                       |                                                              |
| accept-charset | 字符集                     |                                                              |
| action         | 提交目的地 URL             |                                                              |
| method         | 提交方式                   | get、post|
| target         | 打开方式                   | \_blank 、\_self、 \_parent 、\_top                          |
| enctype        | 编码方式                   | application/x-www-form-urlencoded <br/>multipart/form-data <br/>text/plain |
| autocomplete   | 是否启用表单的自动完成功能 |                                                              |
```html
<form action="xxx.php" method="get">
    姓名：<input type="text" name="username" size="15" placeholder="请输入姓名" />
    密码：<input type="password" name="pwd" maxlength="8" placeholder="请输入密码" />
    照片：<input type="file" name="pic" />

    性别：
    <input type="radio" name="sex" value="man" checked/>男
    <input type="radio" name="sex" value="woman" />女

    爱好：
    <input type="checkbox" name="hobby" value="read" checked/>读书
    <input type="checkbox" name="hobby" value="dance" /> 跳舞
    <input type="checkbox" name="hobby" value="sing" /> 唱歌

    城市:
    <select name="city">
        <option value="0" selected>__请选择__</option>
        <optgroup label="北方">
            <option value="bj">北京</option>
            <option value="tj">天津</option>
        </optgroup>
        <optgroup label="南方">
            <option value="gz">广州</option>
            <option value="sz">深圳</option>
        </optgroup>
    </select>
    
    备注：
    <textarea name="tips" cols="5" rows="5">
        这是一段多行文字
    </textarea>
</form>
```



### \<input>

| type     | 描述       |
| -------- | ---------- |
| hidden   | 隐藏       |
| text     | 文本域     |
| password | 密码域     |
| radio    | 单选框     |
| checkbox | 复选框     |
| file     | 文件输入框 |
| image    | 图片输入框 |
| button   | 按钮       |
| reset    | 重置按钮   |
| submit   | 提交按钮   |



| type           | 描述                                                   |
| -------------- | ------------------------------------------------------ |
| number         | 数值输入框                                             |
| date           | 日期输入框                                             |
| color          | 颜色输入框                                             |
| range          | 范围输入框                                             |
| month          | 年月输入框                                             |
| week           | 年周输入框                                             |
| time           | 时间输入框，无时区                                     |
| datetime       | 时间输入框，有时区                                     |
| datetime-local | 时间输入框，日期和时间                                 |
| email          | 邮箱输入框                                             |
| tel            | 电话输入框                                             |
| url            | url输入框                                              |
| search         | 搜索框                                                 |
| ......         | [更多类型](https://www.runoob.com/tags/tag-input.html) |



### \<select>

- 定义下拉列表

```html
<select name="cars">
    <option value="volvo">Volvo</option>
    <option value="saab">Saab</option>
    <option value="fiat">Fiat</option>
    <option value="audi">Audi</option>
</select>
```



### \<textarea>

- 定义多行文本

```html
<textarea name="message" rows="10" cols="30">
	The cat was playing in the garden.
</textarea>
```



### \<button>

- 定义按钮

```html
<button type="button" onclick="alert('Hello World!')">
    Click Me!
</button>
```



### \<datalist>

- 定义选项列表

```html
<input list="browsers" name="browser">
    <datalist id="browsers">
		<option value="Internet Explorer">
      	<option value="Firefox">
      	<option value="Chrome">
      	<option value="Opera">
      	<option value="Safari">
    </datalist>
<input type="submit">
```



## 区块、框架

### \<div>\<span>\<iframe>

| 标签      | 描述                                | 属性          |
| --------- | ----------------------------------- | ------------- |
| \<div>    | 定义了文档的区域，块级              |               |
| \<span>   | 用来组合文档中的行内元素， 内联元素 |               |
| \<iframe> | 定义一个内联的iframe                | width、height |

```html
<div>文档中的块级元素</div>
<span>文档中的内联元素</span>
<iframe src="demo_iframe.htm"></iframe>
```



## 实体

| 转义字符 | 字符  | 转义字符 | 字符   |
| :------- | :---- | :------- | :----- |
| \&nbsp;  | Space | \&quot;  | "      |
| \&lt;    | <     | \&trade; | ™ 商标 |
| \&gt;    | >     | \&reg;   | ® 注册 |
| \&amp;   | &     | \&copy;  | © 版权 |

 
