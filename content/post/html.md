## html

```

<html>
<body background=""></body>

<p>段落
<h1>-<h6> 六级标题
<a>链接
<img />
<br />
<hr /> 标签在 HTML 页面中创建水平线
<table>
<!-- This is a comment -->





浏览器会移除源代码中多余的空格和空行
```
## html文本格式化

``` HTML
<b>
<strong>
<big>
<em>
<i>
<small>
<sub>
<sup>
<pre>


<code>
<kbd>
<samp>
<var>
<tt>

<address>

<abbr> <dfn>
<acronym>

<bdo dir="rtl">

<blockquote>
<q>

<del>		<s>
<ins>		<strike>

<cite>

```


## html元素

HTML 元素指的是从开始标签（start tag）到结束标签（end tag）的所有代码。

- HTML 元素以开始标签起始
- HTML 元素以结束标签终止
- 元素的内容是开始标签与结束标签之间的内容
- 某些 HTML 元素具有空内容（empty content）
- 空元素在开始标签中进行关闭（以开始标签的结束而结束）
- 大多数 HTML 元素可拥有属性


## HTML 属性
HTML 标签可以拥有属性。属性提供了有关 HTML 元素的更多的信息。

属性值应该始终被包括在引号内。双引号是最常用的，不过使用单引号也没有问题。

在某些个别的情况下，比如属性值本身就含有双引号，那么您必须使用单引号，例如：

name='Bill "HelloWorld" Gates'

## HTML样式

1.head引用
```HTML
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
```
2.head内部样式
```
<head>
<style type="text/css">
body {background-color: red}
p {margin-left: 20px}
</style>
</head>
```
3.内联
```
<p style="color: red; margin-left: 20px">
This is a paragraph
</p>
```

```
<div>
<span>

```

## 图像
```html

<img>
<map>
<area>

```


## 表格

<table border="1" cellpadding="20" background="" frame="box">
<tr>
 <th>id</th>
 <th>name</th>
 <th colspan="2">score</th>
</tr>
<tr>
 <td align="">1</td>
 <td>zhang</td>
 <td>80</td>
 <td>90</td>
</tr>
<tr>
 <td>2</td>
 <td>li</td>
 <td> 99</td>
<tr/>
<tr><
 <td>3</td>
 <td>&nbsp;</td>
 <td> 100</td>
</table>

<html>

<body>

<h4>这个表格有一个标题，以及粗边框：</h4>

<table border="6">
<caption>我的标题</caption>
<tr>
  <td>100</td>
  <td>200</td>
  <td>300</td>
</tr>
<tr>
  <td>400</td>
  <td>500</td>
  <td>600</td>
</tr>
</table>

</body>


<table width="100%" border="1">
  <colgroup span="2" align="left"></colgroup>
  <colgroup align="right" style="color:#FF00FF;"></colgroup>
  <tr>
    <th>ISBN</th>
    <th>Title</th>
    <th>Price</th>
  </tr>
  <tr>
    <td>3476896</td>
    <td>My first HTML</td>
    <td>$53</td>
  </tr>
  <tr>
    <td>2489604</td>
    <td>My first CSS</td>
    <td>$47</td>
  </tr>
</table>


## html列表

<ul type="square">
 <li>1</li>
 <li>2</li>
</ul>


<ol>
 <li>AAA</li>
 <li>BBB</li>
</ol>