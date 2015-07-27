title: XHTML+CSS=网站重构-zt
id: 599
categories:
  - 计算机与 Internet
date: 2005-09-16 09:01:12
tags:
---

<div id="msgcns!9697D6160EFEBC17!202" class="bvMsg"><div>

**一，什么是WEB标准？

**WEB标准不是某一个标准，而是一系列标准的集合。网页主要由三部分组成：结构（Structure）、表现（Presentation）和行为（Behavior）。对应的标准也分三方面：结构化标准语言主要包括XHTML和XML，表现标准语言主要包括CSS，行为标准主要包括对象模型（如W3C DOM）、ECMAScript等。这些标准大部分由W3C起草和发布，也有一些是其他标准组织制订的标准，比如ECMA（European Computer Manufacturers Association）的ECMAScript标准。我们来简单了解一下这些标准：

**1．结构标准语言**

（1）XML 

XML是The Extensible Markup Language(可扩展标识语言)的简写。目前推荐遵循的是W3C于2000年10月6日发布的XML1.0，参考（ [<font color="#223355"><u>http://www.w3.org/TR/2000/REC-XML-20001006</u></font>](http://www.w3.org/TR/2000/REC-XML-20001006)  ）。和HTML一样，XML同样来源于SGML，但XML是一种能定义其他语言的语。XML最初设计的目的是弥补HTML的不足，以强大的扩展性满足网络信息发布的需要，后来逐渐用于网络数据的转换和描述。关于XML的好处和技术规范细节这里就不多说了，网上有很多资料，也有很多书籍可以参考。

（2）XHTML 

XHTML是The Extensible HyperText Markup Language可扩展标识语言的缩写。目前推荐遵循的是W3C于2000年1月26日推荐XML1.0（参考 [<font color="#223355"><u>http://www.w3.org/TR/xhtml1</u></font>](http://www.w3.org/TR/xhtml1)  ）。XML虽然数据转换能力强大，完全可以替代HTML，但面对成千上万已有的站点，直接采用XML还为时过早。因此，我们在HTML4.0的基础上，用XML的规则对其进行扩展，得到了XHTML。简单的说，建立XHTML的目的就是实现HTML向XML的过渡。

**2. 表现标准语言**

CSS是Cascading Style Sheets层叠样式表的缩写。目前推荐遵循的是W3C于1998年5月12日推荐CSS2（参考 [<font color="#223355"><u>http://www.w3.org/TR/CSS2/</u></font>](http://www.w3.org/TR/CSS2/)  ）。W3C创建CSS标准的目的是以CSS取代HTML表格式布局、帧和其他表现的语言。纯CSS布局与结构式XHTML相结合能帮助设计师分离外观与结构，使站点的访问及维护更加容易。

**3.行为标准**

（1）DOM

DOM是Document Object Model文档对象模型的缩写。根据W3C DOM规范（ [<font color="#223355"><u>http://www.w3.org/DOM/</u></font>](http://www.w3.org/DOM/)  ），DOM是一种与浏览器，平台，语言的接口，使得你可以访问页面其他的标准组件。简单理解，DOM解决了Netscaped的Javascript和Microsoft的Jscript之间的冲突，给予web设计师和开发者一个标准的方法，让他们来访问他们站点中的数据、脚本和表现层对像。

(2) ECMAScript

ECMAScript是ECMA(European Computer Manufacturers Association)制定的标准脚本语言（JAVAScript）。目前推荐遵循的是ECMAScript 262（ [<font color="#223355"><u>http://www.ecma.ch/ecma1/STAND/ECMA-262.HTM</u></font>](http://www.ecma.ch/ecma1/STAND/ECMA-262.HTM)  ）。

**二、为什么要建立网站标准？**

我们大部分人都有深刻体验，每当主流浏览器版本的升级，我们刚建立的网站就可能变得过时，我们就需要升级或者重新建造一遍网站。例如1996-1999年典型的&quot;浏览器大战&quot;，为了兼容Netscape和IE，网站不得不为这两种浏览器写不同的代码。同样的，每当新的网络技术和交互设备的出现，我们也需要制作一个新版本来支持这种新技术或新设备，例如支持手机上网的WAP技术。类似的问题举不胜举：网站代码臃肿、繁杂浪费了我们大量的带宽；针对某种浏览器的DHTML特效，屏蔽了部分潜在的客户；不易用的代码，残障人士无法浏览网站等等。这是一种恶性循环，是一种巨大的浪费。

如何解决这些问题呢？有识之士早已开始思考，需要建立一种普遍认同的标准来结束这种无序和混乱。商业公司(Netscape、Microsoft等)也终于认识到统一标准的好处，因此在W3C（W3C.org）的组织下，网站标准开始被建立（1998年2月10日发布XML1.0为标志），并在网站标准组织（webstandards.org）的督促下推广执行。

简单说，网站标准的目的就是：

提供最多利益给最多的网站用户 
确保任何网站文挡都能够长期有效 
简化代码、降低建设成本 
让网站更容易使用，能适应更多不同用户和更多网路设备 
当浏览器版本更新，或者出现新的网络交互设备时，确保所有应用能够继续正确执行。 
对于网站设计和开发人员来说，遵循网站标准就是使用标准；对于你的网站用户来说，网站标准就是最佳体验。

**三、采用网站标准有什么好处？**

对网站浏览者的好处：

文件下载与页面显示速度更快； 
内容能被更多的用户所访问（包括失明、视弱、色盲等残障人士）； 
内容能被更广泛的设备所访问（包括屏幕阅读机、手持设备、搜索机器人、打印机、电冰箱等等） 
用户能够通过样式选择定制自己的表现界面 
所有页面都能提供适于打印的版本 

对网站所有者的好处：

更少的代码和组件，容易维护 
带宽要求降低（代码更简洁），成本降低。举个例子：当 ESPN.com 使用 CSS改版后，每天节约超过两兆字节（terabytes）的带宽。 
更容易被搜寻引擎搜索到 
改版方便，不需要变动页面内容 
提供打印版本而不需要复制内容 
提高网站易用性。在美国，有严格的法律条款（Section 508）来约束政府网站必须达到一定的易用性，其他国家也有类似的要求。 

**四、怎么改善现有网站？**

我们大部分的设计师依旧在采用传统的表格布局、表现与结构混杂在一起的方式来建立网站。学习使用XHTML+CSS的方法需要一个过程，使现有网站符合网站标准也不可能一步到位。最好的方法是循序渐进，分阶段来逐步达到完全符合网站标准的目标。如果你是新手，或者对代码不是很熟悉，也可以采用遵循标准的编辑工具，例如Dreamweaver MX 2004，它是目前支持CSS标准最完善的工具。

**1．初级改善**

**为页面添加正确的DOCTYPE **

很多设计师和开发者都不知道什么是DOCTYPE，DOCTYPE有什么用。DOCTYPE是document type的简写。主要用来说明你用的XHTML或者HTML是什么版本。浏览器根据你DOCTYPE定义的DTD(文档类型定义)来解释页面代码。所以，如果你不注意设置了错误的DOCTYPE，结果会让你大吃一惊。XHTML1.0提供了三种DOCTYPE可选择：

(1)过渡型（Transitional ）

&lt;!DOCTYPE html PUBLIC &quot;-//W3C//DTD XHTML 1.0 Transitional//EN&quot; &quot;[<font color="#223355"><u>http://www.w3.org/TR/xhtml1</u></font>](http://www.w3.org/TR/xhtml1) /DTD/xhtml1-transitional.dtd&quot;&gt; 

(2)严格型（Strict ）

&lt;!DOCTYPE html PUBLIC &quot;-//W3C//DTD XHTML 1.0 Strict//EN&quot; &quot;[<font color="#223355"><u>http://www.w3.org/TR/xhtml1</u></font>](http://www.w3.org/TR/xhtml1) /DTD/xhtml1-strict.dtd&quot;&gt; 

(3)框架型（Frameset ）

&lt;!DOCTYPE html PUBLIC &quot;-//W3C//DTD XHTML 1.0 Frameset//EN&quot; &quot;[<font color="#223355"><u>http://www.w3.org/TR/xhtml1</u></font>](http://www.w3.org/TR/xhtml1) /DTD/xhtml1-frameset.dtd&quot;&gt; 

对于我们初级改善来说，只要选用过渡型的声明就可以了。它依然可以兼容你的表格布局、表现标识等，不至于让你觉得变化太大，难以掌握。

Tip:你懒得输入上面过渡型代码的话，可以访问 [<font color="#223355"><u>http://www.macromedia.com/</u></font>](http://www.macromedia.com/)  网站的首页，然后查看源代码，把head区同样的代码拷贝粘贴就可以了。

**设定一个名字空间（Namespace） **

直接在DOCTYPE声明后面添加如下代码：

&lt;html XMLns=&quot;[<u><font color="#0000ff">'&quot; DESIGNTIMESP=32309&gt;</font><font color="#223355">http://www.w3.org/1999/xhtml&quot;&gt;</font></u>](http://www.w3.org/1999/xhtml&quot;&gt;)  

一个namespace是收集元素类型和属性名字的一个详细的DTD，namespace声明允许你通过一个在线地址指向来识别你的namespace。只要照样输入代码就可以。

**声明你的编码语言 **

为了被浏览器正确解释和通过标识校验，所有的XHTML文档都必须声明它们所使用的编码语言。代码如下：

&lt;meta http-equiv=&quot;Content-Type&quot; content=&quot;text/html; charset=GB2312&quot; /&gt; 

这里声明的编码语言是简体中文GB2312，你如果需要制作繁体内容，可以定义为BIG5。

**用小写字母书写所有的标签 **

XML对大小写是敏感的，所以，XHTML也是大小写有区别的。所有的XHTML元素和属性的名字都必须使用小写。否则你的文档将被W3C校验认为是无效的。例如下面的代码是不正确的：

&lt;TITLE&gt;公司简介&lt;/TITLE&gt; 

正确的写法是：

&lt;title&gt;公司简介&lt;/title&gt; 同样的，&lt;P&gt;改成&lt;p&gt;，&lt;B&gt;改成&lt;b&gt;等等。这步转换很简单。 

**为图片添加 alt 属性 **

为所有图片添加alt属性。alt属性指定了当图片不能显示的时候就显示供替换文本，这样做对正常用户可有可无，但对纯文本浏览器和使用屏幕阅读机的用户来说是至关重要的。只有添加了alt属性，代码才会被W3C正确性校验通过。注意的是我们要添加有意义的alt属性，象下面这样的写法毫无意义：

&lt;img src=&quot;logo_unc_120x30.gif&quot; alt=&quot;logo_unc_120x30.gif&quot;&gt; 

正确的写法：

&lt;img src=&quot;logo_unc_120x30.gif&quot; alt=&quot;UNC公司标志，点击返回首页&quot;&gt; 

**给所有属性值加引号 **

在HTML中，你可以不需要给属性值加引号，但是在XHTML中，它们必须被加引号。

例：height=&quot;100&quot;，而不能是height=100。

**关闭所有的标签 **

在XHTML中，每一个打开的标签都必须关闭。就象这样：

&lt;p&gt;每一个打开的标签都必须关闭。&lt;/p&gt; &lt;b&gt;HTML可以接受不关闭的标，XHTML就不可以。&lt;/b&gt; 

这个规则可以避免HTML的混乱和麻烦。举例来说：如果你不关闭图像标签，在一些浏览器中就可能出现CSS显示问题。用这种方法能确保页面和你设计的一样显示。需要说明的是：空标签也要关闭，在标签尾部使用一个正斜杠&quot;/&quot;来关闭它们自己。例如：

&lt;br /&gt; &lt;img src=&quot;webstandards.gif&quot; /&gt; 

经过上述七个规则处理后，页面就基本符合XHTML1.0的要求。但我们还需要校验一下是否真的符合标准了。我们可以利用W3C提供免费校验服务（ [<font color="#223355"><u>http://validator.w3.org/</u></font>](http://validator.w3.org/)  ）。发现错误后逐个修改。在后面的资源列表中我们也提供了其他校验服务和对校验进行指导的网址，可以作为W3C校验的补充。当最后通过了XHTML验证，恭喜你已经向网站标准迈出了一大步。不是想象中的那么难吧！

**2．中级改善**

接下来我们的改善主要在结构和表现相分离上，这一步不象第一步那么容易实现，我们需要观念上的转变，以及对CSS2技术的学习和运用。但学习任何新知识都需要花点时间的，不是吗？诀窍在于边做边学。假如你一直采用表格布局，根本没用过 CSS，也不必急于跟表格布局说再见，你可以先用样式表代替 font 标签。随着你学到的越多，你能做的就越多。好，一起来看看我们需要做哪些事：

**用CSS定义元素外观**

我们在写标识时已经养成习惯，当希望字体大点就用&lt;h1&gt;，希望在前面加个点符号就用&lt;li&gt;。我们总是想&lt;h1&gt;的意思是大的，&lt;li&gt;的意思是圆点，&lt;b&gt;的意思是“加粗文本”。而实际上， &lt;h1&gt;能变成你想要的任何样子，通过CSS，&lt;h1&gt;能变成小的字体，&lt;p&gt;文本能够变成巨大的、粗体的，&lt;li&gt;能够变成一张图片等等。我们不能强迫用结构元素实现表现效果，我们应该使用CSS来确定那些元素的外观。

例如，我们可以使原来默认的6级标题可以看起来大小一样：
h1, h2, h3, h4, h5, h6&#123; font-family: 宋体, serif; font-size: 12px; &#125; 

**用结构化元素代替无意义的垃圾 **

许多人可能从来都不知道HTML和XHTML元素设计本意是用来表达结构的。我们很多人已经习惯用元素来控制表现，而不是结构。例如，一段列表内容可能会使用下面这样的标识：

句子一&lt;br /&gt; 句子二&lt;br /&gt; 句子三&lt;br /&gt; 
如果我们采用一个无序列表代替会更好：
&lt;ul&gt; &lt;li&gt;句子一&lt;/li&gt; &lt;li&gt;句子二&lt;/li&gt; &lt;li&gt;句子三&lt;/li&gt; &lt;/ul&gt; 
你或许会说“但是&lt;li&gt;显示的是一个圆点，我不想用圆点”。事实上，CSS没有设定元素看起来是什么样子，你完全可以用CSS关掉圆点。

**给每个表格和表单加上id **
给表格或表单赋予一个唯一的、结构的标记，例如

&lt;table id=&quot;menu&quot;&gt; 

接下来，在书写样式表的时候，你就可以创建一个“menu”的选择器，并且关联一个CSS规则，用来告诉表格单元、文本标签和所有其他元素怎么去显示。这样，不需要对每个%lt;td&gt;标签附带一些多余的、占用带宽的表现层的高、宽、对齐和背景颜色等等属性。只需要一个附着的标记（标记“menu”的id标记），你就可以在一个分离的样式表内为干净的、紧凑的代码标记进行特别的表现层处理。

中级改善我们这里先列主要的三点，但其中包含的内容和知识点非常多，需要我们逐步学习和掌握，直到最后实现完全采用CSS而不才用任何表格实现布局。**
**

**作者Blog：**[<u><font color="#0000ff">http://blog.csdn.net/godttj/</font></u>](http://blog.csdn.net/godttj/)
</div></div>