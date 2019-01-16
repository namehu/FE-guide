## \<!DOCTYPE html>
> 使用 HTML5 的文档声明类型 : <!DOCTYPE html>

- DOCTYPE标签是一种标准通用标记语言的文档类型声明，它的目的是要告诉标准通用标记语言解析器，它应该使用什么样的文档类型定义（DTD）来解析文档。
- 使用文档声明类型的作用是为了防止开启浏览器的怪异模式。
- 没有DOCTYPE文档类型声明会开启浏览器的怪异模式，浏览器会按照自己的解析方式渲染页面，在不同的浏览器下面会有不同的样式。
- 如果你的页面添加了<!DOCTYP>那么，那么就等同于开启了标准模式。浏览器会按照W3C标准解析渲染页面。


## 页面语言LANG
> Lang属性的取值应该遵循互联网工程任务组–IETF（The Internet Engineering Task Force）制定的关于语言标签的文档

```
// good
<html lang="zh-CN">

// more
zh-SG 中文 (简体, 新加坡)   对应 cmn-Hans-SG 普通话 (简体, 新加坡)
zh-HK 中文 (繁体, 香港)     对应 cmn-Hant-HK 普通话 (繁体, 香港)
zh-MO 中文 (繁体, 澳门)     对应 cmn-Hant-MO 普通话 (繁体, 澳门)
zh-TW 中文 (繁体, 台湾)     对应 cmn-Hant-TW 普通话 (繁体, 台湾)

// deprecated
zh-Hans, zh-Hans-CN, zh-Hans-SG, zh-Hans-HK, zh-Hans-MO, zh-Hans-TW, 
zh-Hant, zh-Hant-CN, zh-Hant-SG, zh-Hant-HK, zh-Hant-MO, zh-Hant-TW
```

## CHARSET
> 默认推荐使用 \<meta charset="UTF-8">


## 脚本加载
> 说到js和css的位置，大家应该都知道js放在下面，css放在上面。
但是，如果你的项目只需要兼容ie10+或者只是在移动端访问，那么可以使用HTML5的新属性async，将脚本文件放在\<head>内

```
// 所以浏览器都推荐
<html>
  <head>
    <link rel="stylesheet" href="main.css">
  </head>
  <body>
    <!-- body goes here -->

    <script src="main.js" async></script>
  </body>
</html>

// 现代浏览器支持
<html>
  <head>
    <link rel="stylesheet" href="main.css">
    <script src="main.js" async></script>
  </head>
  <body>
    <!-- body goes here -->
  </body>
</html>
```

## 资源引用
> 文件名包含多个单词时，单词之间建议使用半角的连词线 ( - ) 分隔

```
// bad
<script src="http://cdn.com/foundation.min.js"></script>

// good
<script src="//cdn.com/foundation.min.js"></script>
```

## 元素及标签闭合
> - 所有具有开始标签和结束标签的元素都要写上起止标签，某些允许省略开始标签或和束标签的元素亦都要写上。
> - 空元素标签都不加 “/” 字符

```
// bad
<div>
    <h1>我是h1标题</h1>
    <p>我是一段文字，我有始无终，浏览器亦能正确解析
</div>

<br/>

// good
<div>
    <h1>我是h1标题</h1>
    <p>我是一段文字，我有始有终，浏览器能正确解析</p>
</div>
	
<br>
```

## 语义化
> 我们一直都在说语义化编程，语义化编程，但是在代码中很少有人完全使用正确的元素。使用语义化标签也是有理由SEO的。

```
// not recommand
<b>My page title</b>
<div class="top-navigation">
  <div class="nav-item"><a href="#home">Home</a></div>
  <div class="nav-item"><a href="#news">News</a></div>
  <div class="nav-item"><a href="#about">About</a></div>
</div>

<div class="news-page">
  <div class="page-section news">
    <div class="title">All news articles</div>
    <div class="news-article">
      <h2>Bad article</h2>
      <div class="intro">Introduction sub-title</div>
      <div class="content">This is a very bad example for HTML semantics</div>
      <div class="article-side-notes">I think I'm more on the side and should not receive the main credits</div>
      <div class="article-foot-notes">
        This article was created by David <div class="time">2014-01-01 00:00</div>
      </div>
    </div>

    <div class="section-footer">
      Related sections: Events, Public holidays
    </div>
  </div>
</div>

<div class="page-footer">
  Copyright 2014
</div>

// good
html 代码:
<!-- The page header should go into a header element -->
<header>
  <!-- As this title belongs to the page structure it's a heading and h1 should be used -->
  <h1>My page title</h1>
</header>

<!-- All navigation should go into a nav element -->
<nav class="top-navigation">
  <!-- A listing of elements should always go to UL (OL for ordered listings) -->
  <ul>
    <li class="nav-item"><a href="#home">Home</a></li>
    <li class="nav-item"><a href="#news">News</a></li>
    <li class="nav-item"><a href="#about">About</a></li>
  </ul>
</nav>

<!-- The main part of the page should go into a main element (also use role="main" for accessibility) -->
<main class="news-page" role="main">
  <!-- A section of a page should go into a section element. Divide a page into sections with semantic elements. -->
  <section class="page-section news">
    <!-- A section header should go into a section element -->
    <header>
      <!-- As a page section belongs to the page structure heading elements should be used (in this case h2) -->
      <h2 class="title">All news articles</h2>
    </header>

    <!-- If a section / module can be seen as an article (news article, blog entry, products teaser, any other
     re-usable module / section that can occur multiple times on a page) a article element should be used -->
    <article class="news-article">
      <!-- An article can contain a header that contains the summary / introduction information of the article -->
      <header>
        <!-- As a article title does not belong to the overall page structure there should not be any heading tag! -->
        <div class="article-title">Good article</div>
        <!-- Small can optionally be used to reduce importance -->
        <small class="intro">Introduction sub-title</small>
      </header>

      <!-- For the main content in a section or article there is no semantic element -->
      <div class="content">
        <p>This is a good example for HTML semantics</p>
      </div>
      <!-- For content that is represented as side note or less important information in a given context use aside -->
      <aside class="article-side-notes">
        <p>I think I'm more on the side and should not receive the main credits</p>
      </aside>
      <!-- Articles can also contain footers. If you have footnotes for an article place them into a footer element -->
      <footer class="article-foot-notes">
        <!-- The time element can be used to annotate a timestamp. Use the datetime attribute to specify ISO time
         while the actual text in the time element can also be more human readable / relative -->
        <p>This article was created by David <time datetime="2014-01-01 00:00" class="time">1 month ago</time></p>
      </footer>
    </article>

    <!-- In a section, footnotes or similar information can also go into a footer element -->
    <footer class="section-footer">
      <p>Related sections: Events, Public holidays</p>
    </footer>
  </section>
</main>

<!-- Your page footer should go into a global footer element -->
<footer class="page-footer">
  Copyright 2014
</footer>
```

## alt永远填入适合的内容
> \<img>标签的 alt 属性指定了替代文本，用于在图像无法显示或者用户禁用图像显示时，代替图像显示在浏览器中的内容。
假设由于下列原因用户无法查看图像，alt 属性可以为图像提供替代的信息：
> - 网速太慢 
> - src 属性中的错误
> - 浏览器禁用图像
> - 用户使用的是屏幕阅读器
> - alt也利于SEO

## HTML代码大小写
> HTML标签名、标签属性和大部分属性值统一用小写.属性值使用kabab-case方式
> id属性可使用underscore方式命名.这带来的好处是。在js文件中可以快速区分class和id。当然。这不强制。只是一个建议。
> *需要注意的是。这个规范在vue组件中会有不同。这个在VUE.md中会进一步说明。

```
// bad
<div class="DEMO"></div>
	
<DIV CLASS="DEMO"></DIV>

// good
<div class="demo" id="my_id"></div>

```

> 一些情况，是不遵循这个规则的
> HTML文本、CDATA、JavaScript、meta标签某些属性等内容可大小写混合

```
<!-- 优先使用 IE 最新版本和 Chrome Frame -->
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"/>

<!-- HTML文本内容 -->
<h1>I AM WHAT I AM </h1>

<!-- JavaScript 内容 -->
<script type="text/javascript">
	var demoName = 'demoName';
	...
</script>
	
<!-- CDATA 内容 -->
<script type="text/javascript"><![CDATA[
...
]]></script>
```

## 元素属性
> - 元素属性值同使用双引号语法
> - 元素属性值尽量填充完整

```
// bad
<input type=text>	
<input type='text'>
	
<input type="radio" name="name" checked >

// godd
<input type="text">
	
<input type="radio" name="name" checked="checked" >
```

## 代码嵌套
> 每个块状元素独立成行，内联元素可选
> 段落与标题元素只能嵌套内联元素

```
// bad
<div>
    <h1></h1><p></p>
</div>	
<p> 
    <span></span>
    <span></span>
</p>

// bad
<h1><div></div></h1>
<p><div></div><div></div></p>

// good
<div>
    <h1></h1>
    <p></p>
</div>	
<p><span></span><span></span></p>

// good
<h1><span></span></h1>
<p><span></span><span></span></p>
```

## 结构、表现、行为三者分离
> 尽量在文档和模板中只包含结构性的 HTML；而将所有表现代码，移入样式表中；将所有动作行为，移入脚本之中。
> - 不使用超过一到两张样式表
> - 不使用超过一到两个脚本（学会用合并脚本）
> - 不使用行内样式（\<style>.no-good {}</style>）
> - 不在元素上使用 style 属性（\<hr style="border-top: 5px solid black">）
> - 不使用行内脚本（\<script>alert('no good')</script>）
> - 不使用表象元素（i.e. \<b>, \<u>, \<center>, \<font>, \<b>）
> - 不使用表象 class 名（i.e. red, left, center）
