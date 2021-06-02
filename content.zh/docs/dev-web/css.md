---
title: "CSS"
date: 2021-01-21T01:01:22+08:00
description: 
enableToc: true
draft: false
weight: 2
---

# CSS 概述

- **层叠样式表**，Cascading Style Sheets
- 简化网页代码，提高页面浏览速度
- 使网页内容与表现相分离



## 继承样式
- html子元素，会继承其父元素的CSS样式



## 层叠样式

- HTML同一元素，可以定义多个样式
- 样式不冲突时，多个样式效果可叠加
- 样式冲突时，按样式的优先级来显示



## 语法规则

- CSS规则，由选择器、声明组成
- 注释：/\*注释语句\*/

![CSS语法](/images/201906/jiandax_20190614100230.png)



## 引入方式

- 外部样式表
- 内部样式表
- 内联样式

```html
//外部样式表：在网页头部引入
<head>
    <link rel="stylesheet" type="text/css" href="XXX.css">
</head>


//内部样式表：在网页头部，定义样式表
<head>
    <style type="text/css">
        p {color:red;}
        ...
    </style>
</head>


//内联颜色表：在相关标签内，定义style属性
<p style="color:red;">这是一个段落。</p>
```



# CSS 基础

## 单位

- **尺寸 - size**

| 值   | 说明               | 备注               |
| ---- | ------------------ | ------------------ |
| %    | 百分比             |                    |
| in   | 英寸               | 25.4 mm            |
| cm   | 厘米               | 10 mm              |
| mm   | 毫米               | 1 mm               |
| pt   | 磅/点，Point       | 0.35 mm            |
| pc   | 派卡，Pica         | 4.23 mm            |
| px   | 像素，Pixel        |                    |
| em   | 当前字体尺寸的倍数 | 1em = 16px（默认） |
| ex   | x-height           | 1ex = 0.5em        |



- **颜色 - color**

| 值              | 说明         | 备注            |
| --------------- | ------------ | --------------- |
| (颜色名)        | 颜色名称     | red             |
| rgb(x,x,x)      | RGB 值       | rgb(255,0,0)    |
| rgb(x%, x%, x%) | RGB 百分比值 | rgb(100%,0%,0%) |
| #rrggbb         | 十六进制数   | #ff0000         |



## 盒模型

- 垂直方向，相邻元素的外边距会合并，实际高度为较大值
- 盒模型各属性，默认不继承父元素样式

![CSS 盒模型](/images/201906/jiandax_20190614114041.png)



## 元素显示

- **display**

| 改变元素类型 | none                                 | 不显示元素 |
| ------------ | ------------------------------------ | ---------- |
| inline       | 显示为内联元素                       |            |
| block        | 显示为块级元素                       |            |
| inline-block | 显示为内联元素，同时具有块级元素特性 |            |

 

- **元素分类**

|                  | 块级元素                                                     | 内联元素                                                     |
| :--------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| 独自占一行       | 是                                                           | 否                                                           |
| 可以包含块级元素 | 是                                                           | 否                                                           |
| 元素宽度         | 与父容器相关                                                 | 与内容相关                                                   |
| 盒模型无效属性   | 无                                                           | width、height、<br/>padding上、margin上下                    |
| 常用元素         | \<div>、\<p>、\<pre>、\<hr>、 <br/>\<h1>~\<h6>、\<form>、列表、表格、... | \<a>、\<b>、\<span>、 <br/>/\<img>、\<input>、\<textarea>、... |

 

## 编写规范

- **CSS 命名**
  - 以小写字母开头
  - 英文字母、数字、"_"、"-"
  - 使用有意义的命名
  - 命名形式：单个单词、连字符、驼峰命名

| 页面结构 | 页头      | header   | 导航                | nav      |
| -------- | --------- | -------- | ------------------- | -------- |
| 页体     | main      | 侧栏     | sidebar             |          |
| 页尾     | footer    | 栏目     | column              |          |
| 内容     | content   | 页面外围 | wrapper             |          |
| 容器     | container | 左中右   | left、center、right |          |
|          |           |          |                     |          |
| 导航     | 主导航    | mainnav  | 边导航              | sidebar  |
| 子导航   | subnav    | 左导航   | leftsidebar         |          |
| 顶导航   | topnav    | 右导航   | rightsidebar        |          |
|          |           |          |                     |          |
| 功能     | 标志      | logo     | 注册                | register |
| 标题     | title     | 搜索     | search              |          |
| 登录     | login     | 广告     | banner              |          |
| 登录条   | loginbar  | 功能区   | shop                |          |

 

- **CSS 书写顺序**
  - 位置：position、top、right、z-index、display、float...
  - 大小：width、height、padding、margin
  - 字体：font、line-height、letter-spacing、color、text-align...
  - 背景：background、border...
  - 其他：animation、transition...



# CSS 选择器

## 基础选择器

| 选择器     | 说明                | CSS       | HTML                    |
| ---------- | ------------------- | --------- | ----------------------- |
| 标签选择器 | 标签名              | p {...}   | \<p>..............\</p> |
| ID选择器   | id属性值，#         | #p1 {...} | \<p id="p1">......\</p> |
| 类选择器   | class属性值， **.** | .c1 {...} | \<p class="c1">...\</p> |



## 派生选择器

| 选择器     | 说明                   | CSS             | HTML                                                  |
| ---------- | ---------------------- | --------------- | ----------------------------------------------------- |
| 全局选择器 | 通配符，*              | *{...}          |                                                       |
| 组合选择器 | 多个选择器，用逗号分隔 | div,p{...}      | \<div>............\</div><br/>\</p>.............\</p> |
| 后代选择器 | 父子标签名，用空格分隔 | div p{...}      | \<div><br/>   \<p>..........\</p><br/> \</div>        |
| 伪类选择器 | 伪类                   | a:visited {...} | \<a ...>..........\</a>                               |



## 伪类

| 伪类         | 说明                   |
| :----------- | :--------------------- |
| :link        | 未被访问的链接         |
| :visited     | 已被访问的链接         |
| :hover       | 鼠标悬浮于上方的元素   |
| :active      | 被激活的元素           |
| :focus       | 拥有键盘输入焦点的元素 |
| :first-child | 元素的第一个子元素     |
| :lang        | 带有lang 属性的元素    |



## 伪元素

| 伪元素        | 说明             |
| :------------ | :--------------- |
| :first-letter | 文本的第一个字母 |
| :first-line   | 文本的首行       |
| :before       | 元素之前         |
| :after        | 元素之后         |

 

## 优先级

- 不同样式表
  - 行内样式>内部样式>外部样式

- 同一样式表
  - 权值相同：就近原则
  - 权值不同：根据权重

| 选择器         | 权重值                                |
| :------------- | :------------------------------------ |
| !important     | 最高，示例：div{color:red !important} |
| 行内样式       | 1000                                  |
| ID选择器       | 100                                   |
| 类选择器、伪类 | 10                                    |
| 标签选择器     | 1                                     |
| 通配符选择器   | 0                                     |



# CSS 样式

## 字体

<table>
	<thead>
		<tr>
			<th scope="col">属性</th>
			<th scope="col">属性说明</th>
			<th scope="col">属性值</th>
			<th scope="col">属性值说明</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>color</td>
			<td>字体颜色</td>
			<td><em>color</em></td>
			<td>颜色值</td>
		</tr>
		<tr>
			<td rowspan="3">font-style</td>
			<td rowspan="3">字体风格</td>
			<td>normal</td>
			<td>正常</td>
		</tr>
		<tr>
			<td>italic</td>
			<td>斜体</td>
		</tr>
		<tr>
			<td>oblique</td>
			<td>斜体</td>
		</tr>
		<tr>
			<td rowspan="5">font-weight</td>
			<td rowspan="5">字体粗细</td>
			<td>100 - 900</td>
			<td>数值：400=normal，700=bold</td>
		</tr>
		<tr>
			<td>lighter</td>
			<td>更细</td>
		</tr>
		<tr>
			<td>normal</td>
			<td>标准</td>
		</tr>
		<tr>
			<td>bold</td>
			<td>粗体</td>
		</tr>
		<tr>
			<td>bolder</td>
			<td>更粗</td>
		</tr>
		<tr>
			<td rowspan="8">font-size</td>
			<td rowspan="8">字体尺寸</td>
			<td><em>size</em></td>
			<td>数值</td>
		</tr>
		<tr>
			<td>
				xx-small
			</td>
			<td>&nbsp;&nbsp;9px</td>
		</tr>
		<tr>
			<td>
				&nbsp;x-small
			</td>
			<td>11px</td>
		</tr>
		<tr>
			<td>
				&nbsp;&nbsp; small
			</td>
			<td>13px</td>
		</tr>
		<tr>
			<td>
                &nbsp; medium
			</td>
			<td>16px</td>
		</tr>
		<tr>
			<td>
				&nbsp;&nbsp; large
			</td>
			<td>19px</td>
		</tr>
		<tr>
			<td>
                &nbsp;x-large
			</td>
			<td>23px</td>
		</tr>
		<tr>
			<td>
                xx-large
			</td>
			<td>28px</td>
		</tr>
		<tr>
			<td rowspan="2">font-family</td>
			<td rowspan="2">字体系列</td>
			<td>字体名</td>
			<td>Times、"Times New Roman"、...</td>
		</tr>
		<tr>
			<td>字体集</td>
			<td>"serif"、"sans-serif"、...</td>
		</tr>
	</tbody>
</table>



- **简写**
  - 顺序：font-style | font-weight | font-size/line-height | font-family
  - 至少需设定 font-size 和 font-family

```css
div{
    font-style:italic;
    font-weight:bold;
    font-size:12px;
    line-height:1.5em;
    font-family:arial,verdana;
    color:red;
}

div{
    font:italic bold 12px/1.5em arial,verdana;
    color:red;
}
```



## 文本

<table>
	<thead>
		<tr>
			<th scope="col">属性</th>
			<th scope="col">属性说明</th>
			<th scope="col">属性值</th>
			<th scope="col">属性值说明</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td rowspan="4">text-align</td>
			<td rowspan="4">水平对齐&nbsp;<br>
			仅对块级元素有效</td>
			<td>left</td>
			<td>左对齐</td>
		</tr>
		<tr>
			<td>center</td>
			<td>居中</td>
		</tr>
		<tr>
			<td>right</td>
			<td>右对齐</td>
		</tr>
		<tr>
			<td>justify</td>
			<td>两端对齐</td>
		</tr>
		<tr>
			<td rowspan="9">vertical-align</td>
			<td rowspan="9">垂直对齐</td>
			<td>baseline</td>
			<td>默认</td>
		</tr>
		<tr>
			<td>sub</td>
			<td>下标</td>
		</tr>
		<tr>
			<td>super</td>
			<td>上标</td>
		</tr>
		<tr>
			<td>top</td>
			<td>最顶端对齐</td>
		</tr>
		<tr>
			<td>text-top</td>
			<td>顶端对齐</td>
		</tr>
		<tr>
			<td>middle</td>
			<td>中部对齐</td>
		</tr>
		<tr>
			<td>bottom</td>
			<td>最底端对齐</td>
		</tr>
		<tr>
			<td>text-bottom</td>
			<td>底端对齐</td>
		</tr>
		<tr>
			<td><em>size</em></td>
			<td>数值</td>
		</tr>
		<tr>
			<td>line-height</td>
			<td>文本行高</td>
			<td><em>size</em></td>
			<td>数值</td>
		</tr>
		<tr>
			<td>word-spacing</td>
			<td>单词间距</td>
			<td><em>size</em></td>
			<td>数值</td>
		</tr>
		<tr>
			<td>letter-spacing</td>
			<td>字符间距</td>
			<td><em>size</em></td>
			<td>数值</td>
		</tr>
		<tr>
			<td>text-indent</td>
			<td>首行缩进</td>
			<td><em>size</em></td>
			<td>数值</td>
		</tr>
		<tr>
			<td rowspan="4">text-transform</td>
			<td rowspan="4">文本大小写</td>
			<td>none</td>
			<td>默认</td>
		</tr>
		<tr>
			<td>capitalize</td>
			<td>单词大写字母开头</td>
		</tr>
		<tr>
			<td>uppercase</td>
			<td>字母都大写</td>
		</tr>
		<tr>
			<td>lowercase</td>
			<td>字母都小写</td>
		</tr>
		<tr>
			<td rowspan="4">text-decoration</td>
			<td rowspan="4">修饰文本</td>
			<td>none</td>
			<td>默认</td>
		</tr>
		<tr>
			<td>underline</td>
			<td>划线，文本底部</td>
		</tr>
		<tr>
			<td>overline</td>
			<td>划线，文本顶部</td>
		</tr>
		<tr>
			<td>line-through</td>
			<td>划线，穿过文本</td>
		</tr>
	</tbody>
</table>



- **文字基线**

![文字基线](/images/201906/jiandax_20190614115620.png)



## 列表

<table>
	<thead>
		<tr>
			<th scope="col">属性</th>
			<th scope="col">属性说明</th>
			<th scope="col">属性值</th>
			<th scope="col">属性值说明</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>list-style</td>
			<td>简写属性</td>
			<td>&nbsp;</td>
			<td>空格分隔各值，不分顺序</td>
		</tr>
		<tr>
			<td rowspan="2">list-style-image</td>
			<td rowspan="2">列表项标志的图片</td>
			<td>none</td>
			<td>无图片，默认</td>
		</tr>
		<tr>
			<td>URL</td>
			<td>图片路径</td>
		</tr>
		<tr>
			<td rowspan="2">list-style-position</td>
			<td rowspan="2">列表项标志的位置</td>
			<td>outside</td>
			<td>标记在文本外，文本与文本对齐。默认</td>
		</tr>
		<tr>
			<td>inside</td>
			<td>标记在文本内，文本与标记对齐</td>
		</tr>
		<tr>
			<td rowspan="9">list-style-type</td>
			<td rowspan="9">列表项标志的类型</td>
			<td>none</td>
			<td>无标记</td>
		</tr>
		<tr>
			<td>disc</td>
			<td>实心圆，默认</td>
		</tr>
		<tr>
			<td>circle</td>
			<td>空心圆</td>
		</tr>
		<tr>
			<td>square</td>
			<td>实心方块</td>
		</tr>
		<tr>
			<td>decimal</td>
			<td>数字</td>
		</tr>
		<tr>
			<td>lower-alpha</td>
			<td>小写英文字母(a、b、c、...)</td>
		</tr>
		<tr>
			<td>upper-alpha</td>
			<td>大写英文字母(A、B、C、...)</td>
		</tr>
		<tr>
			<td>lower-roman</td>
			<td>小写罗马数字(i、ii、iii、...)</td>
		</tr>
		<tr>
			<td>upper-roman</td>
			<td>大写罗马数字(I、II、III、...)</td>
		</tr>
	</tbody>
</table>



## 背景

<table>
	<thead>
		<tr>
			<th scope="col">属性</th>
			<th scope="col">属性说明</th>
			<th scope="col">属性值</th>
			<th scope="col">属性值说明</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>background</td>
			<td>简写</td>
			<td>&nbsp;</td>
			<td>空格分隔各值，不分顺序</td>
		</tr>
		<tr>
			<td rowspan="2">background-color</td>
			<td rowspan="2">背景颜色</td>
			<td>transparent</td>
			<td>透明色，默认</td>
		</tr>
		<tr>
			<td><em>color</em></td>
			<td>颜色值</td>
		</tr>
		<tr>
			<td rowspan="2">background-image</td>
			<td rowspan="2">背景图片</td>
			<td>none</td>
			<td>无图片，默认</td>
		</tr>
		<tr>
			<td>url('<em>URL</em>')</td>
			<td>图片路径</td>
		</tr>
		<tr>
			<td rowspan="4">background-repeat</td>
			<td rowspan="4">背景图片重复</td>
			<td>repeat</td>
			<td>默认。垂直方向及水平方向重复</td>
		</tr>
		<tr>
			<td>repeat-x</td>
			<td>水平方向重复</td>
		</tr>
		<tr>
			<td>repeat-y</td>
			<td>垂直方向重复</td>
		</tr>
		<tr>
			<td>no-repeat</td>
			<td>不重复</td>
		</tr>
		<tr>
			<td rowspan="2">background-attachment</td>
			<td rowspan="2">背景图片滚动</td>
			<td>scroll</td>
			<td>跟随滚动。默认</td>
		</tr>
		<tr>
			<td>fixed</td>
			<td>固定</td>
		</tr>
		<tr>
			<td rowspan="8">background-position</td>
			<td rowspan="8">背景图片起始位置</td>
			<td colspan="2">当只有一个值时，第二个值默认为居中</td>
		</tr>
		<tr>
			<td>x%、y%</td>
			<td>百分比，默认0% 0%</td>
		</tr>
		<tr>
			<td>x、y</td>
			<td>数值</td>
		</tr>
		<tr>
			<td>top</td>
			<td>上</td>
		</tr>
		<tr>
			<td>bottom</td>
			<td>下</td>
		</tr>
		<tr>
			<td>left</td>
			<td>左</td>
		</tr>
		<tr>
			<td>right</td>
			<td>右</td>
		</tr>
		<tr>
			<td>center</td>
			<td>中</td>
		</tr>
	</tbody>
</table>



```css
body{ 
    background-image:url('/i/eg_bg_03.gif');
    background-repeat:no-repeat;
    background-position:66% 33%;
}
```



# CSS 位置

## 边框

<table>
	<thead>
		<tr>
			<th scope="col">属性</th>
			<th scope="col">属性说明</th>
			<th scope="col">属性值</th>
			<th scope="col">属性值说明</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>border</td>
			<td>简写属性</td>
			<td colspan="2">border: [宽度] [样式] [颜色]</td>
		</tr>
		<tr>
			<td>border-width | style | color</td>
			<td>简写属性</td>
			<td colspan="2">&nbsp;</td>
		</tr>
		<tr>
			<td>border-left | right | top | bottom</td>
			<td>简写属性</td>
			<td colspan="2">&nbsp;</td>
		</tr>
		<tr>
			<td rowspan="4">border-[ left | right | top | bottom ]-width</td>
			<td rowspan="4">边框宽度</td>
			<td>thin</td>
			<td>细边框</td>
		</tr>
		<tr>
			<td>medium</td>
			<td>中边框，默认</td>
		</tr>
		<tr>
			<td>thick</td>
			<td>粗边框</td>
		</tr>
		<tr>
			<td><em>size</em></td>
			<td>数值</td>
		</tr>
		<tr>
			<td rowspan="10">border-[ left | right | top | bottom ]-style</td>
			<td rowspan="10">边框样式</td>
			<td>none</td>
			<td>无边框</td>
		</tr>
		<tr>
			<td>hidden</td>
			<td>无边框，用于解决边框冲突</td>
		</tr>
		<tr>
			<td>dotted</td>
			<td>点状边框</td>
		</tr>
		<tr>
			<td>dashed</td>
			<td>虚线边框</td>
		</tr>
		<tr>
			<td>solid</td>
			<td>实线边框</td>
		</tr>
		<tr>
			<td>double</td>
			<td>双线边框</td>
		</tr>
		<tr>
			<td>groove</td>
			<td>3D 凹槽边框</td>
		</tr>
		<tr>
			<td>ridge</td>
			<td>3D 垄状边框</td>
		</tr>
		<tr>
			<td>inset</td>
			<td>3D inset 边框</td>
		</tr>
		<tr>
			<td>outset</td>
			<td>3D outset 边框</td>
		</tr>
		<tr>
			<td rowspan="2">border-[ left | right | top | bottom ]-color</td>
			<td rowspan="2">边框颜色</td>
			<td>transparent</td>
			<td>透明色，默认</td>
		</tr>
		<tr>
			<td><em>color</em></td>
			<td>颜色值</td>
		</tr>
	</tbody>
</table>



## 边距

<table>
	<tbody>
		<tr>
			<td>padding</td>
			<td>padding-left | right | top | bottom</td>
			<td>内边距</td>
		</tr>
		<tr>
			<td>margin</td>
			<td>margin-left | right | top | bottom</td>
			<td>外边距</td>
		</tr>
		<tr>
			<td rowspan="2">值</td>
			<td>auto</td>
			<td>浏览器自动计算</td>
		</tr>
		<tr>
			<td><em>size</em></td>
			<td>数值</td>
		</tr>
		<tr>
			<td rowspan="4">简写&nbsp;<br>
			助记：顺时针</td>
			<td>margin:值1</td>
			<td>上下左右 = 值1</td>
		</tr>
		<tr>
			<td>margin:值1 值2</td>
			<td>上下=值1，左右=值2</td>
		</tr>
		<tr>
			<td>margin:值1 值2 值3</td>
			<td>上=值1，左右=值2，下=值3</td>
		</tr>
		<tr>
			<td>margin:值1 值2 值3 值4</td>
			<td>上=值1，右=值2，下=值3，左=值4</td>
		</tr>
	</tbody>
</table>



## 宽高

| 属性       | 属性说明 |
| :--------- | :------- |
| width      | 宽度     |
| min-width  | 最小宽度 |
| max-width  | 最大宽度 |
| height     | 高度     |
| min-height | 最小高度 |
| max-height | 最大高度 |

| 属性值  | 属性值说明 |
| :------ | :--------- |
| auto    | 默认       |
| *size*  | 数值       |
| inherit | 继承       |

 

## 定位

<table>
	<thead>
		<tr>
			<th scope="col">属性</th>
			<th scope="col">属性说明</th>
			<th scope="col">属性值</th>
			<th scope="col">属性值说明</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td rowspan="5">position</td>
			<td rowspan="5">定位</td>
			<td>static</td>
			<td>没有定位，默认值</td>
		</tr>
		<tr>
			<td>fixed</td>
			<td>绝对定位，相对于浏览器窗口，脱离标准流</td>
		</tr>
		<tr>
			<td>absolute</td>
			<td>绝对定位，相对于父元素，脱离标准流</td>
		</tr>
		<tr>
			<td>relative</td>
			<td>相对定位，相对于自身正常位置</td>
		</tr>
		<tr>
			<td>inherit</td>
			<td>继承</td>
		</tr>
		<tr>
			<td rowspan="3">z-index</td>
			<td rowspan="3">层级</td>
			<td>auto</td>
			<td>与父元素相等，默认</td>
		</tr>
		<tr>
			<td><em>number</em></td>
			<td>层级数值</td>
		</tr>
		<tr>
			<td>inherit</td>
			<td>继承</td>
		</tr>
		<tr>
			<td rowspan="3">top&nbsp;<br>
			bottom&nbsp;<br>
			left&nbsp;<br>
			right</td>
			<td rowspan="3">上下左右</td>
			<td>auto</td>
			<td>浏览器计算，默认</td>
		</tr>
		<tr>
			<td><em>size</em></td>
			<td>数值</td>
		</tr>
		<tr>
			<td>inherit</td>
			<td>继承</td>
		</tr>
	</tbody>
</table>



## 浮动

<table>
	<thead>
		<tr>
			<th scope="col">属性</th>
			<th scope="col">属性说明</th>
			<th scope="col">属性值</th>
			<th scope="col">属性值说明</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td rowspan="4">float</td>
			<td rowspan="4">浮动</td>
			<td>none</td>
			<td>不浮动，默认</td>
		</tr>
		<tr>
			<td>left</td>
			<td>左浮动</td>
		</tr>
		<tr>
			<td>right</td>
			<td>右浮动</td>
		</tr>
		<tr>
			<td>inherit</td>
			<td>继承</td>
		</tr>
		<tr>
			<td rowspan="5">clear</td>
			<td rowspan="5">清除浮动</td>
			<td>none</td>
			<td>两侧元素，允许浮动，默认值。</td>
		</tr>
		<tr>
			<td>left</td>
			<td>左侧元素，不允许浮动</td>
		</tr>
		<tr>
			<td>right</td>
			<td>右侧元素，不允许浮动</td>
		</tr>
		<tr>
			<td>both</td>
			<td>两侧元素，不允许浮动</td>
		</tr>
		<tr>
			<td>inherit</td>
			<td>继承</td>
		</tr>
	</tbody>
</table>



- **浮动规则**
  - 浮动元素
    - 不会重叠 
    - 不会上下浮动 
    - 会脱离标准流
  - 浮动元素的外边距，不会超过父元素内边距
  - 非浮动元素的文本，会环绕浮动元素周围

