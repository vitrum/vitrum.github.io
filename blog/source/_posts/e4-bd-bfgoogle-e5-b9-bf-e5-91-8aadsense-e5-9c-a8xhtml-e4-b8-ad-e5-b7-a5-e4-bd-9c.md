title: 使Google广告AdSense在XHTML中工作
id: 500
categories:
  - 计算机与 Internet
date: 2005-11-15 08:39:14
tags:
---

<div id="msgcns!9697D6160EFEBC17!380" class="bvMsg"><div>

# [http://www.omemo.net/neo/tech/adsense.php](http://www.omemo.net/neo/tech/adsense.php)

[<u><font color="#0000ff">主页</font></u>](http://spaces.msn.com/) &gt; [<u><font color="#0000ff">设计与技术</font></u>](http://spaces.msn.com/neo/tech/) &gt; [<u><font color="#0000ff">使Google广告AdSense在XHTML中工作</font></u>](http://spaces.msn.com/mmm2005-10-24_14.28/adsense.php)

<div>
<div>
<div>

### 翻译手记

我开始使用XHTML 1.1的时候，发现Google的AdSense广告在IE上正常，在Firefox和Opera中则一片空白，纳闷，对着代码检查了良久，终究无法得知问题于何处。幸亏还有Google，我终于找到这个解决方案。我也不能不说，推广标准，还真的是任重道远，连Google都无法保证它的代码会在任何的(X)HTML上工作。

这其实是一个JavaScript的问题，假如你发现你在XHTML 1.0 Stric或者XHTML 1.1中无法使用JavaScript的调用，或许，这篇文章对你也有启示。
</div>

## 为什么AdSense不能在真正的XHTML中工作？

Google的[<u><font color="#0000ff">AdSense</font></u>](https://www.google.com/adsense/afc-online-overview "Google AdSense：概述")使用JavaScript生成一个`iframe`来动态地发送广告。如果页面是使用常规的<abbr title="Hypertext Markup Language">HTML</abbr>或者不严格版本的XHTML，以`text/html`来伺服的话，没有任何问题。这个JavaScript如你所愿地生成`iframe`，任何事情都工作得很好。不幸的是，对于站长以`application/xhtml+xml`来伺服的XHTML，Google的方法不能工作。

主要问题出在JavaScript。`Document.Write()`不会在正确伺服的由一个<abbr title="Extensible Markup Language">XML</abbr>解析器处理的XML页面中工作。Ian Hickson给出了为什么会这样的[<u><font color="#0000ff">理由</font></u>](http://ln.hixie.ch/?start=1091626816&amp;count=1 "Hixie:  Why document.write() doesn")（中文版本站已经翻译：[<u><font color="#0000ff">为什么`document.write`在XML中不工作</font></u>](http://spaces.msn.com/neo/tech/dw_not_work.php)）。就如我们所觉察到的，`Document.Write()`用来生成`iframe`，因此，Google的广告永远不会出现。

第二个问题在于`iframe`本身。这个元素没有出现在任何严格的XHTML版本中，所以尽管JavaScript可以生成，`iframe`会使这个页面的XHTML不合法。

## 怎么才能使它工作呢？

解决这些问题的一条途径是，简单地以`text/html`来伺服AdSense代码。为达到目的，有必要创建一个独立的网页，使用`text/html`的<acronym title="Multipurpose Internet Mail Extension">MIME</acronym>类型，然后以`object`的形式插入到需要的页面中。下面是一个独立的文档的样例：
<pre>&lt;!DOCTYPE html PUBLIC &quot;-//W3C//DTD HTML 4.01 Transitional//EN&quot; &quot;http://www.w3.org/TR/html4/loose.dtd&quot;&gt;
&lt;html lang=&quot;en&quot;&gt;
&lt;head&gt;
&lt;title&gt;Sponsorship&lt;/title&gt;
&lt;style type=&quot;text/css&quot;&gt;
body &#123; margin: 0; padding: 0; &#125;
&lt;/style&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;script type=&quot;text/javascript&quot;&gt;
这里是Google AdSense的参数
&lt;/script&gt;
&lt;script type=&quot;text/javascript&quot; src=&quot;http://pagead2.googlesyndication.com/pagead/show_ads.js&quot;&gt;&lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;</pre>

对于使用这个[<u><font color="#0000ff">分离内容和MIME内容脚本</font></u>](http://spaces.msn.com/neo/tech/mime_type.php "使用正确的MIME类型伺服XHTML")来同时伺服`application/xhtml+xml`和`text/html`的站长，最好能够利用已经存在的代码来决定这两种不同的方法的采用。在原始的分离内容和MIME内容脚本中，MIME类型由`$mime`变量来保存。如果该变量的值是“application/xhtml+xml”，则可以在文档中使用`object`。否则，则把标准AdSense的JavaScript包含进来。下面的脚本演示这是如何做到的：
<pre> &lt;div class=&quot;ads&quot;&gt;
&lt;?php
if($mime == &quot;application/xhtml+xml&quot;) &#123; print &quot; &lt;object data=&quot;/includes/google.php&quot; type=&quot;text/html&quot;&gt;&lt;/object&gt;n&quot;;
&#125; else &#123;
?&gt;
&lt;script type=&quot;text/javascript&quot;&gt;

这里是Google AdSense的参数 
&lt;/script&gt;
&lt;script type=&quot;text/javascript&quot; src=&quot;http://pagead2.googlesyndication.com/pagead/show_ads.js&quot;&gt;&lt;/script&gt;
&lt;?php
&#125;
?&gt;
&lt;/div&gt;</pre>

这个解决方案业已在IE 6， [<u><font color="#0000ff">Firefox</font></u>](http://www.spreadfirefox.com/?q=affiliates&amp;id=38491&amp;t=72) 0.92和Opera 7.0中测试通过。
</div></div></div></div>