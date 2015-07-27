title: IE默认input按钮的常见问题 - 转贴
id: 288
categories:
  - 计算机与 Internet
date: 2007-02-28 15:11:55
tags:
---

<div id="msgcns!9697D6160EFEBC17!963" class="bvMsg"><div>出处:http://www.planabc.net/article.asp?id=81</div>
<div>原作者:[<u><font color="#0000ff">Blank</font></u>](http://vitrum.spaces.live.com/mmm2007-02-10_13.26/user.asp?act=view&amp;id=1)</div>
<div> </div>
<div>在制作按钮的时候大家一般都很头疼，经常会出现这样那样问题，搞得很烦恼，那对于IE默认情况下的input按钮我们经常会碰见那些问题呢？下面列举了一些出现几率比较高的问题：

一、IE默认按钮的value值，每增加4个字节（汉字为2个）时，就会在按钮的两边产生总共一个字节的内边距宽度。

二、XP风格的IE默认按钮样式是一个固定尺寸的圆角矩形图片作背景，一旦按钮变宽变高后，这个固定尺寸的圆角矩形图片的边缘会出现“拉毛”现象。

三、当你触发按钮的时候，会出现1px的黑色的外边框，在input的bordor属性的外面。

[蓝色](http://www.blueidea.com/ "http://www.blueidea.com/")论坛[标准版](http://bbs.blueidea.com/forum-5-1.html "http://bbs.blueidea.com/forum-5-1.html")版主zbm2001z 针对上面的一和二问题，提出了一个解决方案：

<div>&lt;!-- IE Quirks mode --&gt;
&lt;!DOCTYPE html PUBLIC &quot;-//W3C//DTD XHTML 1.0 Transitional//EN&quot; &quot;http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd&quot;&gt;
&lt;html xmlns=&quot;http://www.w3.org/1999/xhtml&quot;&gt;
&lt;head&gt;
&lt;meta http-equiv=&quot;Content-Type&quot; content=&quot;text/html; charset=gb2312&quot; /&gt;
&lt;style type=&quot;text/css&quot;&gt;
*&#123;font-size:12px;&#125;
.button,.button input&#123;
  display:-moz-inline-box;
  display:inline-block;
  background-image:url(http://bbs.blueidea.com/attachments/2006/12/25/add_ZKfMl3JpD868.png);
&#125;
.button&#123;
  margin:auto 1%;
  padding-right:3px;
  background-position:100% 0;
&#125;
.button input&#123;
  padding:1px 3px 3px 15px;
  _padding:3px 0 0 12px;
  border:0;
  text-align:center;
&#125;
label.button:hover,.button:hover&#123;
  background-position:100% 100%;
&#125;
label.button:hover input,.button:hover input&#123;
  background-position:0 100%;
  color:#f00;
&#125;
@media all and(min-width:0px)&#123;/* opera 7 styles */
  .button input&#123;padding:4px 6px 4px 18px;&#125;
&#125;
&lt;/style&gt;
&lt;title&gt;&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;label class=&quot;button&quot;&gt;
&lt;input type=&quot;button&quot; value=&quot;永远爱我的老婆-赜赜！&quot; /&gt;
&lt;/label&gt;
&lt;script type=&quot;text/javascript&quot;&gt;
var nav=navigator.appVersion;
if (nav.indexOf('MSIE')!=-1)&#123;
  var input=document.getElementsByTagName(&quot;input&quot;);
  for(var i=0; i&lt;input.length; i++)&#123;
    var inputs=input[i];
    if(inputs.type==&quot;button&quot;)&#123;
      var inputL=inputs.value.replace(/[^x00-xff]/g,'**').length;
      if(inputL&gt;4)&#123;
        var iCFS=inputs.currentStyle.fontSize.substring(0,2);
        inputs.style.width=inputs.clientWidth-((inputL-4)*iCFS/4)+&quot;px&quot;;
      &#125;
    &#125;
  &#125;
&#125;
&lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;</div>
**CSS要点提示：**

1、display:-moz-inline-box;为Firefox的私有属性。

2、background-position:x y;第一个值用于横坐标，第二个值用于纵坐标。

3、下划线（_padding:3px 0 0 12px;），可参看Blank翻译的文章[《翻译:The Underscore Hack》](http://www.planabc.net/article.asp?id=28 "http://www.planabc.net/article.asp?id=28")

4、opera进行特殊控制可以用：

@media all and (min-width: 0px) &#123;

#选择器 &#123;
CSS代码
&#125;
&#125;

此方法里的属性仅针对opera有效,其它浏览器不识别,所以有时候当opera浏览器和别的浏览器不兼容的时候我们就可以用这种方面来进行调整。</div></div>