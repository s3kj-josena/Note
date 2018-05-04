**HTML是网页内容的载体**

内容就是网页制作者放在页面上想要让用户浏览的信息，可以包含文字、图片、视频等。

**CSS样式是表现**

就像网页的外衣。比如，标题字体、颜色变化，或为标题加入背景图片、边框等。所有这些用来改变内容外观的东西称之为表现。

**JavaScript是用来实现网页上的特效效果**

如：鼠标滑过弹出下拉菜单。或鼠标滑过表格的背景颜色改变。还有焦点新闻（新闻图片）的轮换。可以这么理解，有动画的，有交互的一般都是用JavaScript来实现的。

**标签：**

标题标签：**&lt;hx&gt;**标题文本&lt;/hx&gt;   （h1——h6分别为一级标题到六级标题，h1是最高等级）

段落标签：**&lt;p&gt;**段落文本&lt;/p&gt;

图片标签：**&lt;img **src="xxx.jpg"&gt;

强调标签：**&lt;strong&gt;**&lt;/strong&gt;   更强烈的强调，默认**粗体**表示。

强调：**&lt;em&gt;**&lt;/em&gt;  默认**斜体表示。**

**&lt;span&gt;**标签：设置单独的样式。

```
<html>
<head>
<style>
span{color:red;}   /*设置样式*/
</style>
</head>
<body>
<p>...<span>...</span>...</p>  /*标签*/
</body>
</html>
```

**&lt;q&gt; **标签：短文本引用。&lt;q&gt;引用文本&lt;/q&gt;（要引用的文本不用加双引号，浏览器会对q标签自动添加双引号）

**&lt;blockquote&gt;**标签：长文本引用。（浏览器对该标签的解析是缩进样式）

**&lt;br /&gt;**标签：分行显示文本。（在 html 代码中输入回车、空格都是无效的，要换行必须输入&lt;br /&gt;）

**   **：空格。

**&lt;hr /&gt; **：添加水平横线。

**&lt;address&gt; **：为网页加入地址信息。&lt;address&gt;联系地址信息&lt;/address&gt;

**&lt;code&gt; **：加入一行代码

```
<code>代码语言</code>
如：<code>var i=i+300;</code>
```

**&lt;pre&gt; **：加入大段代码。

```
<pre>语言代码段</pre>
如：
<pre>
    var message="欢迎";
    for(var i=1;i<=10;i++){
        alert(message);
    }
</pre>
```

**&lt;ul&gt; **：添加信息列表。

```
<ul>
    <li>信息</li>
    <li>信息</li>
    ... ...
</ul>
ul-li是没有前后顺序的信息列表，显示的默认样式为每项 li 前都自带一个原点。
```

有序的列表：

```
<ol>
    <li>信息</li>
    <li>信息</li>
    ... ...
</ol>
<ol>在网页中显示的默认样式一般为每项 li 前都自带一个序号，从1开始。
```

**&lt;div&gt; **：把一些独立的逻辑部分划分出来，放在一个 &lt;div&gt; 标签中，这个标签的作用相当于一个容器。

```
<div>...</div>
（红色边框）
```

给 **div 命名**，使逻辑更加清晰：用** id **属性来为 &lt;div&gt; 提供唯一的名称。

```
<div id="版块名称">...</div>
```

**&lt;table&gt; ：**表格。

```
<table>
    <tr>    /*表格的行，有几对<tr></tr>就有几行
        <th>表头1</th>
        <th>表头2</th>
    </tr>
    <tr>
        <td>列1的值</td>
        <td>列2的值</td>    /*一行中包含几对<td></td>就有几列
    </tr>
</table>
```

创建表格的四个元素：**table 、tbody 、tr 、th 、td**

**&lt;tbody&gt;…&lt;/tbody&gt;：**如果不加&lt;thead&gt;&lt;tbody&gt;&lt;tfooter&gt; , table表格加载完后才显示。加上这些表格结构， tbody包含行的内容下载完优先显示，不必等待表格结束后在显示，同时如果表格很长，用tbody分段，可以一部分一部分地显示。（通俗理解table 可以按结构一块块的显示，不在等整个表格加载完后显示。）

**用 CSS 样式，为表格加入边框：**

```
<style type="text/css">
    /*为 th,td 单元格添加粗细为一个像素的黑色边框*/
    table tr td,th{border:1px solid #000;}
</style>
```

**caption 标签，为表格添加标题和摘要：**

**摘要**的内容不会在浏览器中显示出来，作用是增加表格的可读性（语义化）。

```
<table summary="表格简介文本">
```

**标题**是用以描述表格内容，显示位置：表格上方。

```
<table>
    <caption>标题文本</caption>
    <tr>
        <td>...</td>
        ...
    </tr>
    ...
</table>
```

**&lt;a&gt; 标签：**实现超链接。

```
<a href="目标网址" title="鼠标滑过显示的文本">链接显示的文本</a>
```

title属性的作用，鼠标滑过链接文字时会显示这个属性的文本内容。这个属性在实际网页开发中作用很大，主要方便搜索引擎了解链接地址的内容（语义化更友好）。

**在新建浏览器窗口中打开链接：**

&lt;a&gt; 标签在默认情况下，链接的网页是在当前浏览器窗口打开，如果需要在新的浏览器窗口中打开：

```
<a href="目标网址" target="_blank">click here!</a>
```

**使用 mailto 在网页中链接 Email 地址：**

邮箱地址\(收件人\)：mailto:

抄送地址：cc=

密件抄送地址：bcc=

邮件主题：subject=

邮件内容：body=

如果 mailto 后面有多个参数，第一个必须以" ? "开头，后面每一个参数都以" & "分隔。

```
<a href="mailto:shoujianren@imooc.com ? cc=chaosong@imooc.com 
& bcc=mijian@imooc.com & subject=主题 & body=邮件内容">发送</a>

点击发送就会自动填写收件人等设置好的信息。
```

**&lt;img&gt; 标签：**为网页插入图片

```
<img src="图片地址" alt="下载失败时的替换文本" title="提示文本">

举例：<img src="myimage.gif" alt="加载失败" title="这是我的图片" />
src : 标识图像的位置
alt : 指定图像的描述性文本，当图像不可见时，可看到该属性指定的文本
title : 提供在图像可见时对图像的描述（鼠标滑过图片时显示的文本）
图像可以是 GIF、PNG、JPEG 格式的图像文件。
```

**使用表单标签，与用户交互：**

表单是可以把浏览者输入的数据传送到服务器端，这样服务器端程序就可以处理表单传过来的数据。

```
<form method="传送方式" action="服务器文件">
```

**&lt;form&gt;** ：&lt;form&gt;标签是成对出现的，以&lt;form&gt;开始，以&lt;/form&gt;结束。

**action **：浏览者输入的数据被传送到的地方，比如一个 PHP 页面\(save.php\)。

**method **：数据传送的方式（get/post）。

```
<form  method="post" action="save.php">
    <label for="username">用户名：
    </label>
    <input typa="text" name="username" />
    <label for="pass">密码：
    </label>
    <input type="password" name="pass" />
</form>
```

**文本输入框、密码输入框：**

```
<form>
    <input type="text/password" name="名称" value="文本" />
</form>
```

**type **：当 type="**text**" 时，输入框为**文本输入框**；当 type="**password**" 时，输入框为**密码输入框**。

**name **：为文本框命名，以备后台程序 ASP、PHP 使用。

**value **：为文本输入框设置默认值（一般起到提示作用）。

```
<form>
    姓名：
    <input type="text" name="myName">
    <br />
    密码：
    <input type="password" name="pass">
</form>
```

**文本域**：支持多行文本输入。

```
<textarea rows="行数" cols="列数">文本</textarea>
```

在 &lt;textarea&gt;&lt;/textarea&gt; 标签之间可以输入默认值：

```
<form method="post" action="save.php">
    <label>联系我们</label>
    <textarea cols="50" rows="10" >在这里输入内容...
    </textarea>
</form>
```

**单选框、复选框：**

```
<input type="radio/checkbox" value="值" name="名称" checked="checked"/>
```

**type **：当 type="**radio**" 时，控件为**单选框**；当 type="**checkbox**" 时，控件为**复选框**。

**value **：提交数据到服务器的值（后台程序 PHP 使用）。

**name **：为控件命名，以备后台程序 ASP、PHP 使用。

**checked **：当设置 checked="checked" 时，该选项被默认选中。

注意：同一组的单选按钮，name 取值一定要一致。

**下拉列表框：**节省空间。

```
<form name="iForm">
    <label>爱好：</label>
    <select>
        <option value="提交值">选项</option>
        ...
        <option value="xxx">xx</option>
        <option value="购物" selected="selected" >购物</option>
    </select>
</form>
```

提交值：向服务器提交的值

选项：显示的值

selected="selected" ：设置该属性，则该选项就被默认选中。

**下拉列表框（多选）：**

在 &lt;select&gt; 开始标签中设置 multiple="multiple" 属性，可实现多选功能。

```
<form name="iForm">
    <label>爱好：</label>
    <select multiple="multiple">
        <option value="xx">xx</option>
        ...
    </select>
</form>
```

**提交按钮：**

```
<input type="submit" value="提交">
```

type ：只有当 type 的值设置为 submit 时，按钮才有提交功能。

value ：按钮上显示的字。

**重置按钮：**

```
<input type="reset" value="重置">
```

**form 表单中的 label 标签：**

当用户单击选中该label标签时，浏览器就会自动将焦点转到和标签相关的表单控件上（就自动选中和该label标签相关连的表单控件上）。

```
<label for="控件 id 名称">
```

注意：标签的 for 属性中的值应当与相关控件的 id 属性值一定要相同。

```
<form>
    <label for="male">男</label>
    <input tyoe="radio" name="gender" id="male" />
    <br />
    <label for="female">女</label>
    <input type="radio" name="gender" id="female" />
    <br />
    <label for="email">输入你的邮箱地址</label>
    <input type="email" id="email" placeholder="Enter email">
</form>
```

**认识 html 文件基本结构：**

```
<html>
    <head>...</head>
    <body>...</body>
</html>
```

* &lt;html&gt;&lt;/html&gt; 为跟标签，所有的网页标签都在&lt;html&gt;&lt;/html&gt;中。
* &lt;head&gt;标签定义文档的头部，是所有头部元素的容器。头部元素有 &lt;title&gt; 、&lt;script&gt; 、&lt;style&gt; 、&lt;link&gt; 、&lt;meta&gt; 等标签。
* 在 &lt;body&gt; 和 &lt;/body&gt; 标签之间的内容是网页的主要内容。如 &lt;h1&gt; 、&lt;p&gt; 、&lt;a&gt; 、&lt;img&gt; 等网页内容标签，在这里的标签中的内容会在浏览器中显示出来。

**认识 head 标签：**

文档的头部描述了文档的各种属性和信息，包括文档的标题等。绝大多数文档头部包含的数据不会显示给读者。

```
<head>
    <title>...</title>
    <meta>
    <link>
    <style>...</style>
    <script>...</script>
</head>
```

**&lt;title&gt; **标签：其中的文字内容是网页的标题信息，会出现在浏览器的标题栏中。用于告诉用户和搜索引擎这个网页的主要内容。

**HTML 的代码注释：**

```
<!--注释文字-->
```

**CSS 注释代码：**

```
/*注释文字*/
```

**认识 CSS 样式：**

CSS全称为“层叠样式表 \(Cascading Style Sheets\)”，它主要是用于定义HTML内容在浏览器内的显示样式，如文字大小、颜色、字体加粗等。

通过定义某个样式，可以让不同网页位置的文字有着统一的字体、字号或者颜色等。

```
p{
    font-size:12px;     /*字体大小*/
    color:red;          /*字体颜色*/
    font-weight:bold;   /*加粗*/
}
```

**CSS** 样式由**选择符**和**声明**组成，而声明又由**属性**和**值**组成。——选择符{ 属性:值;属性:值;... }

**CSS 样式基本知识：**

**内联式：**把css代码直接写在现有的HTML标签中（注意要写在元素的开始标签里）。

```
<p style="color:red;font-size:12px">这里文字是红色。</p>
```

**嵌入式：**嵌入式css样式必须写在&lt;style&gt;&lt;/style&gt;之间，并且一般情况下写在&lt;head&gt;&lt;/head&gt;之间。

```
<head>
    <style type="text/css">
        span{color:red;}
    </style>
</head>
```

**外部式\(外联式\)：**把css代码写一个单独的外部文件中，这个css样式文件以“.css”为扩展名，在&lt;head&gt;内（不是在&lt;style&gt;标签内）使用&lt;link&gt;标签将css样式文件链接到HTML文件内。

```
<head>
    <link href="bass.css" rel="stylesheet" type="text/css" />
</head>
```

注意：

* css 样式文件名称以有意义的英文字母命名，如 main.css 。
* rel="stylesheet" type="text/css" 是固定写法，不可修改。
* &lt;link&gt; 标签位置一般写在 &lt;head&gt; 标签之内。

**优先级：就近原则**\(离被设置元素越近优先级越高\)

内联式 &gt; 嵌入式 &gt; 外部式 \(但是嵌入式&gt;外部式有一个前提：嵌入式的位置一定在外部式的后面\)。

**选择器：**

在{}之前的部分就是“选择器”，“选择器”指明了{}中的“样式”的作用对象，也就是“样式”作用于网页中的哪些元素。

```
选择器{
    样式；
}
```

**标签选择器：**

标签选择器其实就是html代码中的标签。如&lt;html&gt;、&lt;body&gt;、&lt;h1&gt;、&lt;p&gt;、&lt;img&gt;、&lt;span&gt;等。

```
p{......;} /
span{......;}
```

**类选择器：**

类选择器在css样式编码中是最常用到的

```
.类选器名称{css 样式代码;}
```

* 英文圆点开头"."
* 类选器名称可以任意起名（但不要起中文）

* 使用合适的标签把要修饰的内容标记起来。

* 使用 class="类选器名称"为标签设置一个类。
* 设置类选器 css 样式。

**ID选择器：**













在这一章节我们要开始把网页中常用到的标签一 一向大家介绍，学习这一章节的时候要记住学习html标签过程中，主要注意两个方面的学习：标签的用途、标签在浏览器中的默认样式。

**标签的用途**：我们学习网页制作时，常常会听到一个词，**语义化**。那么什么叫做语义化呢，说的通俗点就是：明白每个标签的用途（在什么情况下使用此标签合理）比如，网页上的文章的**标题**就可以用标题标签，网页上的各个栏目的**栏目名称**也可以使用标题标签。文章中内容的段落就得放在**段落标签**中，在文章中有想强调的文本，就可以使用 em 标签表示强调等等。

讲了这么多语义化，但是语义化可以给我们带来什么样的好处呢？

1. 更容易被搜索引擎收录。

2. 更容易让屏幕阅读器读出网页内容。

在后面的章节会带领大家学习了解html中每个标签的语义（用途）。在这一章节我们要开始把网页中常用到的标签一 一向大家介绍，学习这一章节的时候要记住学习html标签过程中，主要注意两个方面的学习：标签的用途、标签在浏览器中的默认样式。

**标签的用途**：我们学习网页制作时，常常会听到一个词，**语义化**。那么什么叫做语义化呢，说的通俗点就是：明白每个标签的用途（在什么情况下使用此标签合理）比如，网页上的文章的**标题**就可以用标题标签，网页上的各个栏目的**栏目名称**也可以使用标题标签。文章中内容的段落就得放在**段落标签**中，在文章中有想强调的文本，就可以使用 em 标签表示强调等等。

讲了这么多语义化，但是语义化可以给我们带来什么样的好处呢？

1. 更容易被搜索引擎收录。

2. 更容易让屏幕阅读器读出网页内容。

在后面的章节会带领大家学习了解html中每个标签的语义（用途）。在这一章节我们要开始把网页中常用到的标签一 一向大家介绍，学习这一章节的时候要记住学习html标签过程中，主要注意两个方面的学习：标签的用途、标签在浏览器中的默认样式。

**标签的用途**：我们学习网页制作时，常常会听到一个词，**语义化**。那么什么叫做语义化呢，说的通俗点就是：明白每个标签的用途（在什么情况下使用此标签合理）比如，网页上的文章的**标题**就可以用标题标签，网页上的各个栏目的**栏目名称**也可以使用标题标签。文章中内容的段落就得放在**段落标签**中，在文章中有想强调的文本，就可以使用 em 标签表示强调等等。

讲了这么多语义化，但是语义化可以给我们带来什么样的好处呢？

1. 更容易被搜索引擎收录。

2. 更容易让屏幕阅读器读出网页内容。

在后面的章节会带领大家学习了解html中每个标签的语义（用途）。在这一章节我们要开始把网页中常用到的标签一 一向大家介绍，学习这一章节的时候要记住学习html标签过程中，主要注意两个方面的学习：标签的用途、标签在浏览器中的默认样式。

**标签的用途**：我们学习网页制作时，常常会听到一个词，**语义化**。那么什么叫做语义化呢，说的通俗点就是：明白每个标签的用途（在什么情况下使用此标签合理）比如，网页上的文章的**标题**就可以用标题标签，网页上的各个栏目的**栏目名称**也可以使用标题标签。文章中内容的段落就得放在**段落标签**中，在文章中有想强调的文本，就可以使用 em 标签表示强调等等。

讲了这么多语义化，但是语义化可以给我们带来什么样的好处呢？

1. 更容易被搜索引擎收录。

2. 更容易让屏幕阅读器读出网页内容。

在后面的章节会带领大家学习了解html中每个标签的语义（用途）。

