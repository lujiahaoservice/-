#杭州翰库前端代码风格规范

1. [规范概述](#intro)
2. [基本信息](#profile)
3. [通用约定](#general)
	* [文档目录结构](#directory)
	* [分离](#separate)
	* [文件命名](#file-name)
	* [缩进](#indentation)
	* [编码](#encoding)
	* [小写](#lowercase)
	* [注释](#comment)
	* [待办事项](#todo)
	* [省略嵌入式资源协议头](#protocol-relative-url)
4. [HTML](#html)
	* [语法](#html-general)
	* [HTML doctype](#doctype)
	* [语言属性](#lang)
	* [IE 兼容模式](#ie)
	* [字符编码](#charset)
	* [引入 CSS 和 JavaScript 文件](#links)
	* [属性顺序](#attr)
	* [布尔（boolean）型属性](#boolean)
	* [减少标签的数量](#less-tag)	
5. [CSS](#css) 
	* [语法](#css-general)
	* [声明顺序](#order)
	* [媒体查询（Media query）的位置](#media-query)
	* [带前缀的属性](#prefix)
	* [单行规则声明](#one-line)
	* [简写形式的属性声明](#short)
	* [Less 和 Sass 中的嵌套](#nest)
	* [注释](#css-comment)
	* [class 命名](#class-name)
	* [选择器](#selector)
6. [JavaScript](#javascript)
	* [变量](#var)
	* [常量](#const)
	* [分号](#semicolon)
	* [多行字符串](#multi-line-string)
	* [命名](#name)
	* [大括号](#brackets)
	* [缩进](#indentation)
	* [空行](#space-line)
	* [引号](#quotation-mark)
	* [注释](#javascript-comment)
7. [图像](#img)
	* [图像压缩](#img-compress)
	* [背景图](#background-image)
	* [前景图](#image)
	* [Sprite](#sprite)	
8. [参考资料](#reference)

<a name="intro"></a>
##规范概述

规范的制定是我们长期以来对工作的积累与沉淀的产物，帮助我们更快、更好、更高效的完成繁重、复杂、多样化的任务，我们制作规范的主要目的在于：

* 降低每个组员介入项目的门槛成本；
* 提高工作效率及协同开发的便捷性；
* 高度统一的代码风格；
* 提供一整套HTML、CSS解决方案，来帮助开发人员快速做出高质量的符合要求的页面。

<a name="profile"></a>
## 基本信息

规范名称 | Cook
--------|------|
当前版本 | v1.0 beta
规范发起 | [胡炜轩(@huweixuan)](http://weibo.com/hwxkyon)
参与人群 | Bilibili的前端工程师们
最后更新 | 2015.06.30

<a name="general"></a>
## 通用约定

<a name="directory"></a>
### 1.文档目录结构

//TODO

<a name="separate"></a>
### 2.分离

结构（HTML）、表现（CSS）、行为分离（JavaScript）

> 将结构与表现、行为分离，保证它们之间的最小耦合，这对前期开发和后期维护都至关重要。

<a name="file-name"></a>
### 3.文件命名

CSS模块文件，其文件名必须与模块名一致；假定有这样一个模块：

	.m-detail { sRules; }
	.m-detail-hd { sRules; }
	.m-detail-bd { sRules; }
	.m-detail-ft { sRules; }

那么该模块的文件名应该为：`m-detail.css`

CSS页面文件，其文件名必须与HTML文件名一致；假定有一个HTML页面叫 `product.html`，那么其相对应的CSS页面文件名应该为：`product.css`

假定现在有一个 `product.html`，里面有2个模块：

	<section class="m-list">
	<section class="m-info">

那么开发人员能快速找到与该页面相关的3个直接CSS文件，包括：`product.css`, `m-list.css`, `m-info.css`

<a name="indentation"></a>
### 4.缩进

将你的编辑器按照下面的配置进行设置，以避免常见的代码不一致和差异：

用四个空格代替制表符（soft-tab 即用空格代表 tab 符）。
保存文件时，删除尾部的空白符。
设置文件编码为 UTF-8。
在文件结尾添加一个空白行。

推荐使用sublime text来进行前端脚本的编写。

可以在Preferences -> Setting - User 中加入以下配置:

	"tab_size": 4,
	"translate_tabs_to_spaces": true

此时，按tab键即可敲出四个空格。

<a name="encoding"></a>
### 5.编码

* 以 UTF-8 无 BOM 编码作为文件格式；
* 在HTML中文档中用 `<meta charset="utf-8" />` 来指定编码；
* 为每个CSS文档显示的定义编码，在文档首行定义 `@charset "utf-8";`

在 Sass 中，如果文档中出现中文，却未显示定义编码，将会编译出错，为了统一各种写法，且提前规避错误几率，统一要求每个CSS文档都需要定义编码

<a name="lowercase"></a>
### 6.小写

所有的HTML标签必须小写；

所有的HTML属性必须小写；

所有的样式名及规则必须小写。

<a name="comment"></a>
### 7.注释

好的命名与代码组织优于注释。如果你为代码添加了注释，在对代码进行改动的时候记得更新它。

<a name="todo"></a>
### 8.待办事项

用 TODO 标示待办事项和正在开发的条目

	<!-- TODO: 图文混排 -->
	<div class="g-imgtext">
	<img src="1.png" alt="" />
	...

	/* TODO: 图文混排 comm: g-imgtext */
	.g-imgtext { sRules; }

<a name="protocol-relative-url"></a>
### 9.省略嵌入式资源协议头

省略图像、媒体文件、样式表和脚本等URL协议头部声明 ( http: , https: )。如果不是这两个声明的URL则不省略。

省略协议声明，使URL成相对地址，防止内容混淆问题和导致小文件重复下载（这个主要是指http和https交杂的场景中）。

不推荐：

	<script src="http://www.google.com/js/gweb/analytics/autotrack.js"></script>

推荐：

	<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>

不推荐：

```
.example {
  background: url(http://www.google.com/images/example);
}
```

推荐：

```
.example {
  background: url(//www.google.com/images/example);
}
```

> 注：省略协议头在IE7-8下会有一点小问题，外部CSS文件（link和@import）会被下载两遍，所以该条目的约定看具体项目。

<a name="html"></a>
##HTML

<a name="html-general"></a>
###语法

用两个空格来代替制表符（tab） -- 这是唯一能保证在所有环境下获得一致展现的方法。

嵌套元素应当缩进一次（即两个空格）。

对于属性的定义，确保全部使用双引号，绝不要使用单引号。

不要在自闭合（self-closing）元素的尾部添加斜线 -- HTML5 规范中明确说明这是可选的。

不要省略可选的结束标签（closing tag）（例如，</li> 或 </body>）。

	<!DOCTYPE html>
	<html>
  	  <head>
    	<title>Page title</title>
  	  </head>
  	  <body>
        <img src="images/company-logo.png" alt="Company">
        <h1 class="hello-world">Hello, world!</h1>
  	  </body>
    </html>

<a name="doctype"></a>
###HTML5 doctype

为每个 HTML 页面的第一行添加标准模式（standard mode）的声明，这样能够确保在每个浏览器中拥有一致的展现。

	<!DOCTYPE html>
	<html>
  	  <head>
  	  </head>
	</html>

<a name="lang"></a>
###语言属性

根据 HTML5 规范：

强烈建议为 html 根元素指定 lang 属性，从而为文档设置正确的语言。这将有助于语音合成工具确定其所应该采用的发音，有助于翻译工具确定其翻译时所应遵守的规则等等。

	<html lang="zh-CN">
      <!-- ... -->
	</html>

<a name="ie"></a>
###IE 兼容模式

IE 支持通过特定的 <meta> 标签来确定绘制当前页面所应该采用的 IE 版本。除非有强烈的特殊需求，否则最好是设置为 edge mode，从而通知 IE 采用其所支持的最新的模式。

	<meta http-equiv="X-UA-Compatible" content="IE=Edge/">

<a name="charset"></a>
###字符编码

通过明确声明字符编码，能够确保浏览器快速并容易的判断页面内容的渲染方式。这样做的好处是，可以避免在 HTML 中使用字符实体标记（character entity），从而全部与文档编码一致（一般采用 UTF-8 编码）。

	<head>
      <meta charset="UTF-8">
	</head>

<a name="links"></a>
###引入 CSS 和 JavaScript 文件

根据 HTML5 规范，在引入 CSS 和 JavaScript 文件时一般不需要指定 type 属性，因为 text/css 和 text/javascript 分别是它们的默认值。

	<!-- External CSS -->
	<link rel="stylesheet" href="code-guide.css">

	<!-- In-document CSS -->
	<style>
  	  /* ... */
	</style>

	<!-- JavaScript -->
	<script src="code-guide.js"></script>

<a name="attr"></a>
###属性顺序

HTML 属性应当按照以下给出的顺序依次排列，确保代码的易读性。

	class
	id, name
	data-*
	src, for, type, href
	title, alt
	aria-*, role
	
> class 用于标识高度可复用组件，因此应该排在首位。id 用于标识具体组件，应当谨慎使用（例如，页面内的书签），因此排在第二位。

	<a class="..." id="..." data-modal="toggle" href="#">
  	  Example link
	</a>

	<input class="form-control" type="text">

	<img src="..." alt="...">

<a name="boolean"></a>
###布尔（boolean）型属性

布尔型属性不用赋值。

	<input type="text" disabled>
	
	<input type="checkbox" value="1" checked>
	
	<select>
      <option value="1" selected>1</option>
	</select>

<a name="less-tag"></a>
###减少标签的数量

编写 HTML 代码时，尽量避免多余的父元素。

	<!-- Not so great -->
	<span class="avatar">
      <img src="...">
	</span>

	<!-- Better -->
	<img class="avatar" src="...">

<a name="css"></a>
##CSS

<a name="css-general"></a>
###语法

用两个空格来代替制表符（tab）。这是唯一能保证在所有环境下获得一致展现的方法。

为选择器分组时，将单独的选择器单独放在一行。

为了代码的易读性，在每个声明块的左花括号前添加一个空格。

声明块的右花括号应当单独成行。

每条声明语句的 : 后应该插入一个空格。

为了获得更准确的错误报告，每条声明都应该独占一行。

所有声明语句都应当以分号结尾。最后一条声明语句后面的分号是可选的，但是，如果省略这个分号，你的代码可能更易出错。

对于以逗号分隔的属性值，每个逗号后面都应该插入一个空格（例如，box-shadow）。

不要在 rgb()、rgba()、hsl()、hsla() 或 rect() 值的内部的逗号后面插入空格。这样利于从多个属性值（既加逗号也加空格）中区分多个颜色值（只加逗号，不加空格）。

对于属性值或颜色参数，省略小于 1 的小数前面的 0 （例如，.5 代替 0.5；-.5px 代替 -0.5px）。

十六进制值应该全部小写，例如，#fff。在扫描文档时，小写字符易于分辨，因为他们的形式更易于区分。

尽量使用简写形式的十六进制值，例如，用 #fff 代替 #ffffff。

为选择器中的属性添加双引号，例如，input[type="text"]。只有在某些情况下是可选的，但是，为了代码的一致性，建议都加上双引号。

避免为 0 值指定单位，例如，用 margin: 0; 代替 margin: 0px;。

	/* Bad CSS */
	.selector, .selector-secondary, .selector[type=text] {
  	  padding:15px;
      margin:0px 0px 15px;
  	  background-color:rgba(0, 0, 0, 0.5);
  	  box-shadow:0px 1px 2px #CCC,inset 0 1px 0 #FFFFFF
	}

	/* Good CSS */
	.selector,
	.selector-secondary,
	.selector[type="text"] {
  	  padding: 15px;
  	  margin-bottom: 15px;
  	  background-color: rgba(0,0,0,.5);
  	  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
	}

<a name="order"></a>
###声明顺序

相关的属性声明应当归为一组，并按照下面的顺序排列：

	Positioning
	Box model
	Typographic
	Visual

> 由于定位（positioning）可以从正常的文档流中移除元素，并且还能覆盖盒模型（box model）相关的样式，因此排在首位。盒模型排在第二位，因为它决定了组件的尺寸和位置。

> 其他属性只是影响组件的内部（inside）或者是不影响前两组属性，因此排在后面。

	.declaration-order {
  	  /* Positioning */
  	  position: absolute;
  	  top: 0;
  	  right: 0;
  	  bottom: 0;
  	  left: 0;
  	  z-index: 100;

  	  /* Box-model */
  	  display: block;
  	  float: right;
  	  width: 100px;
  	  height: 100px;

  	  /* Typography */
  	  font: normal 13px "Helvetica Neue", sans-serif;
  	  line-height: 1.5;
  	  color: #333;
  	  text-align: center;

  	  /* Visual */
  	  background-color: #f5f5f5;
  	  border: 1px solid #e5e5e5;
  	  border-radius: 3px;

  	  /* Misc */
  	  opacity: 1;
	}

<a name="media-query"></a>	
###媒体查询（Media query）的位置

将媒体查询放在尽可能相关规则的附近。不要将他们打包放在一个单一样式文件中或者放在文档底部。如果你把他们分开了，将来只会被大家遗忘。下面给出一个典型的实例。

	.element { ... }
	.element-avatar { ... }
	.element-selected { ... }

	@media (min-width: 480px) {
  	  .element { ...}
      .element-avatar { ... }
      .element-selected { ... }
	}

<a name="prefix"></a>		
###带前缀的属性

当使用特定厂商的带有前缀的属性时，通过缩进的方式，让每个属性的值在垂直方向对齐，这样便于多行编辑。

> 在 Sublime Text 2 中，使用 Selection → Add Previous Line (⌃⇧↑) 和 Selection → Add Next Line (⌃⇧↓)。

	/* Prefixed properties */
	.selector {
  	  -webkit-box-shadow: 0 1px 2px rgba(0,0,0,.15);
          	  box-shadow: 0 1px 2px rgba(0,0,0,.15);
	}

<a name="one-line"></a>	
###单行规则声明

对于只包含一条声明的样式，为了易读性和便于快速编辑，建议将语句放在同一行。对于带有多条声明的样式，还是应当将声明分为多行。

> 这样做的关键因素是为了错误检测。例如，CSS 校验器指出在 183 行有语法错误。如果是单行单条声明，你就不会忽略这个错误；如果是单行多条声明的话，你就要仔细分析避免漏掉错误了。

	/* Single declarations on one line */
	.span1 { width: 60px; }
	.span2 { width: 140px; }
	.span3 { width: 220px; }

	/* Multiple declarations, one per line */
	.sprite {
 	  display: inline-block;
  	  width: 16px;
  	  height: 15px;
  	  background-image: url(../img/sprite.png);
	}
	.icon           { background-position: 0 0; }
	.icon-home      { background-position: 0 -20px; }
	.icon-account   { background-position: 0 -40px; }

<a name="short"></a>		
###简写形式的属性声明

在需要显示地设置所有值的情况下，应当尽量限制使用简写形式的属性声明。常见的滥用简写属性声明的情况如下：

	padding
	margin
	font
	background
	border
	border-radius

> 大部分情况下，我们不需要为简写形式的属性声明指定所有值。例如，HTML 的 heading 元素只需要设置上、下边距（margin）的值，因此，在必要的时候，只需覆盖这两个值就可以。过度使用简写形式的属性声明会导致代码混乱，并且会对属性值带来不必要的覆盖从而引起意外的副作用。

	/* Bad example */
	.element {
  	  margin: 0 0 10px;
  	  background: red;
  	  background: url("image.jpg");
  	  border-radius: 3px 3px 0 0;
	}

	/* Good example */
  	.element {
  	  margin-bottom: 10px;
  	  background-color: red;
  	  background-image: url("image.jpg");
      border-top-left-radius: 3px;
      border-top-right-radius: 3px;
	}

<a name="nest"></a>
###Less 和 Sass 中的嵌套

避免非必要的嵌套。这是因为虽然你可以使用嵌套，但是并不意味着应该使用嵌套。只有在必须将样式限制在父元素内（也就是后代选择器），并且存在多个需要嵌套的元素时才使用嵌套。

	// Without nesting
	.table > thead > tr > th { … }
	.table > thead > tr > td { … }

	// With nesting
	.table > thead > tr {
 	  > th { … }
  	  > td { … }
	}
	
<a name="css-comment"></a>		
###注释

好的class名称优于注释。过去的css注释多数用来区分功能块，现在可以用sass、less等模块化的css预处理器来拆分。

<a name="class-name"></a>
###class 命名

class 名称中只能出现小写字符和破折号（dashe）（不是下划线，也不是驼峰命名法）。破折号应当用于相关 class 的命名（类似于命名空间）（例如，.btn 和 .btn-danger）。

避免过度任意的简写。.btn 代表 button，但是 .s 不能表达任何意思。
class 名称应当尽可能短，并且意义明确。

使用有意义的名称。使用有组织的或目的明确的名称，不要使用表现形式（presentational）的名称。

基于最近的父 class 或基本（base） class 作为新 class 的前缀。
使用 .js-* class 来标识行为（与样式相对），并且不要将这些 class 包含到 CSS 文件中。

在为 Sass 和 Less 变量命名是也可以参考上面列出的各项规范。

	/* Bad example */
	.t { ... }
	.red { ... }
	.header { ... }

	/* Good example */
	.tweet { ... }
	.important { ... }
	.tweet-header { ... }
	
<a name="selector"></a>
###选择器

对于通用元素使用 class ，这样利于渲染性能的优化。

对于经常出现的组件，避免使用属性选择器（例如，[class^="..."]）。浏览器的性能会受到这些因素的影响。

选择器要尽可能短，并且尽量限制组成选择器的元素个数，建议不要超过 3 。

只有在必要的时候才将 class 限制在最近的父元素内（也就是后代选择器）（例如，不使用带前缀的 class 时，前缀类似于命名空间）。

	/* Bad example */
	span { ... }
	.page-container #stream .stream-item .tweet .tweet-	header .username { ... }
	.avatar { ... }

	/* Good example */
	.avatar { ... }
	.tweet-header .username { ... }
	.tweet .avatar { ... }	

<a name="javascript"></a>
##JavaScript规范

<a name="var"></a>
###变量

声明变量必须加上 var 关键字。

> 当你没有写 var，变量就会暴露在全局上下文中，这样很可能会和现有变量冲突。另外，如果没有加上，很难明确该变量的作用域是什么，变量也很可能像在局部作用域中，很轻易地泄漏到 Document 或者 Window 中，所以务必用 var 去声明变量。

<a name="const"></a>
###常量

常量的形式如: NAMES_LIKE_THIS， 即使用大写字符，并用下划线分隔。

<a name="semicolon"></a>
###分号

总是使用分号。不解释。

<a name="multi-line-string"></a>
###多行字符串

不要使用。请使用前端模板。

> 不要这样写长字符串:

	var myString = 'A rather long string of English text, an error message \
                actually that just keeps going and going -- an error \
                message to make the Energizer bunny blush (right through \
                those Schwarzenegger shades)! Where was I? Oh yes, \
                you\'ve got an error and all the extraneous whitespace is \
                just gravy.  Have a nice day.';

<a name="name"></a>
###命名

通常，使用 functionNamesLikeThis，variableNamesLikeThis，ClassNamesLikeThis，EnumNamesLikeThis，methodNamesLikeThis，和 SYMBOLIC_CONSTANTS_LIKE_THIS。

注:
 
* 1.文件或类中的 私有 属性，变量和方法名应该以下划线 "_" 开头。
* 2.保护 属性，变量和方法名不需要下划线开头，和公共变量名一样。

<a name="brackets"></a>
###大括号

分号会被隐式插入到代码中，所以你务必在同一行上插入大括号。例如：

	if (something) {
  	  // ...
	} else {
      // ...
	}

<a name="indentation"></a>
###缩进

大多数代码使用两个空格而不是制表符来进行缩进。

除了 初始化数组和对象，和传递匿名函数外，所有被拆开的多行文本要么选择与之前的表达式左对齐，要么以4个(而不是2个)空格作为一缩进层次。

> 如果初始值不是很长，就保持写在单行上：

	var arr = [1, 2, 3];  // No space after [ or before ].
	var obj = {a: 1, b: 2, c: 3};  // No space after { or before }.
> 初始值占用多行时，缩进2个空格。

	// Object initializer.
	var inset = {
  	  top: 10,
      right: 20,
      bottom: 15,
      left: 12
    };

	// Array initializer.
	this.rows_ = [
  	  '"Slartibartfast" <fjordmaster@magrathea.com>',
  	  '"Zaphod Beeblebrox" <theprez@universe.gov>',
  	  '"Ford Prefect" <ford@theguide.com>',
  	  '"Arthur Dent" <has.no.tea@gmail.com>',
  	  '"Marvin the Paranoid Android" <marv@googlemail.com>',
  	  'the.mice@magrathea.com'
	];

	// Used in a method call.
	goog.dom.createDom(goog.dom.TagName.DIV, {
  	  id: 'foo',
  	  className: 'some-css-class',
  	  style: 'display:none'
	}, 'Hello, world!');
	
> 比较长的标识符或者数值, 不要为了让代码好看些而手工对齐. 如:

	CORRECT_Object.prototype = {
  	  a: 0,
  	  b: 1,
  	  lengthyName: 2
	};
	
> 不要这样做:

	WRONG_Object.prototype = {
  	  a          : 0,
  	  b          : 1,
  	  lengthyName: 2
	};

<a name="space-line"></a>
###空行

使用空行来划分一组逻辑上相关联的代码片段。

	doSomethingTo(x);
	doSomethingElseTo(x);
	andThen(x);

	nowDoSomethingWith(y);

	andNowWith(z);

<a name="quotation-mark"></a>
###引号

使用 ' 优于 "。

> 当你创建一个包含 HTML 代码的字符串时就知道它的好处了。

	var msg = 'This is some HTML';

<a name="javascript-comment"></a>
###注释

好的函数命名与参数命名优于注释。如果你特别喜爱写注释，请使用[JSDoc](http://usejsdoc.org/)中的注释风格。行内注释使用 // 变量 的形式。

<a name="img"></a>
## 图像

<a name="img-compress"></a>
### 图像压缩

所有图片必须经过一定的压缩和优化才能发布

<a name="background-image"></a>
### 背景图

使用PNG格式而不是GIF格式，因为PNG格式色彩更丰富，还能提供更好的压缩比；

<a name="image"></a>
### 前景图

内容图片建议使用JPG，可以拥有更好地显示效果；装饰性图片使用PNG。

<a name="sprite"></a>
### Sprite

CSS Sprite是一种将数个图片合成为一张大图的技术（既可以是背景图也可以是前景图），然后通过偏移来进行图像位置选取；CSS Sprite可以减少http请求。

<a name="reference"></a>
##参考资料

* [google javascript style guide](http://alloyteam.github.io/JX/doc/specification/google-javascript.xml#JavaScript_%E7%BC%96%E7%A0%81%E9%A3%8E%E6%A0%BC)

* [bootstrap code guide](http://codeguide.bootcss.com/)


	

