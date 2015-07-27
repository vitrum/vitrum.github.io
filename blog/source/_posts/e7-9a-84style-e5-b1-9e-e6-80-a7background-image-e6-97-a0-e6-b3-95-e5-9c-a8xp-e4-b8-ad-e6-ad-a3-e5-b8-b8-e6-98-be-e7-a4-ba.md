title: 的style属性background-image无法在xp中正常显示
id: 245
categories:
  - 计算机与 Internet
date: 2007-06-03 03:43:14
tags:
---

<div id="msgcns!9697D6160EFEBC17!1088" class="bvMsg"><div>转贴:地址:http://bestcomy.cnblogs.com/archive/2004/08/30/37614.html</div>
<div> </div>
<div>
<p>问题重现:
<p>&lt;input style=&quot;BACKGROUND-POSITION: center center; BACKGROUND-IMAGE: url(../Images/search.gif); WIDTH: 25px; BACKGROUND-REPEAT: no-repeat;&quot; type=&quot;button&quot;&gt;
<p>在w2k中用ie浏览能够正常显示，而在wxp中用ie浏览则无法正常显示。
<p>解决：
<p>此问题通过咨询[<u><font color="#0000ff">dudu</font></u>](http://www.cnblogs.com/dudu)得到解决，解决办法很简单,为style增加background-color属性，具体如下:
&lt;input style=&quot;BACKGROUND-POSITION: center center; BACKGROUND-IMAGE: url(../Images/search.gif); BACKGROUND-COLOR: buttonface; WIDTH: 25px; BACKGROUND-REPEAT: no-repeat;&quot; type=&quot;button&quot;&gt;
<p>目前还不知道是何原因，知道的朋友请指点一下，不知道的朋友更值得注意一下这个问题。
<p> 
<p>这个是XP样式应用于IE中的策略问题。 

通常，如果XP认为控件的STYLE和XP样式不冲突，那么就按XP的样式来显示控件。 
如果改变控件的BORDER，颜色等因数，那么XP就取消该控件的XP样式。 
所以上面设置bgcolor是生效的。 
至于bgimage为什么不行，我想是开发人员没有对这个处理吧。 
</div></div>