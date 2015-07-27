title: CSS控制连接阴影字
id: 261
categories:
  - 计算机与 Internet
date: 2007-04-28 08:04:30
tags:
---

<div id="msgcns!9697D6160EFEBC17!1053" class="bvMsg"><div> </div>
<div> </div>
<div>&lt;html&gt;
&lt;head&gt;
&lt;meta http-equiv=&quot;Content-Type&quot; content=&quot;text/html; charset=utf-8&quot;&gt;
&lt;style type=&quot;text/css&quot;&gt;
span&#123;font-size:12px;&#125;
span#001 &#123;
 position:absolute;
 cursor: hand;
 font-size:14px;
 padding:0px;
&#125;
span#002 &#123;
    position:absolute;
 font-size:18px;
 cursor: hand;
    padding:0px;
 color:#000099;
    filter:dropshadow(color=#ef0000,offx=1,offy=1,positive=2);
&#125;
span#003 &#123;
    position:absolute;
 cursor: hand;
 font-size:14px;
    padding:0px;
 color:#ff0099;
    filter:dropshadow(color=#ef0000,offx=1,offy=1,positive=2);
&#125;</div>
<div>body,td,th &#123;
 font-size: 14px;
&#125;
body &#123;
 margin-left: 0px;
 margin-top: 0px;
&#125;
&lt;/style&gt;
　　　&lt;/head&gt;
　　　&lt;body&gt;
&lt;script language=javascript&gt;
  var lastid;
  var foreid='002';
  var clickid='003';
  function mouseOnIt(obj)&#123;
   if(obj.id!=clickid)&#123;
    lastid=obj.id;
    obj.id=foreid;
   &#125;
  &#125;
  function mouseOutIt(obj)&#123;
   if(obj.id!=clickid)&#123;
    obj.id=lastid;
   &#125;
  &#125;
  function mouseClick(obj)&#123;
   if(obj.id!=clickid)&#123;
    obj.id=clickid;
   &#125;else&#123;
    obj.id=foreid;
   &#125;
  &#125;
&lt;/script&gt;</div>
<div>&lt;br&gt;&lt;span id=&quot;001&quot;&gt;吃饱穿暖吃饱喝足吃饱喝足迟&lt;/span&gt;
&lt;br&gt;&lt;br&gt;&lt;br&gt;&lt;br&gt;
&lt;a href=&quot;####&quot;&gt;&lt;span id=&quot;001&quot; onmouseover=mouseOnIt(this) onmouseout=mouseOutIt(this) onclick=mouseClick(this)&gt;吃饱穿暖吃饱喝足吃饱喝足迟&lt;/span&gt;&lt;/a&gt;</div>
<div>&lt;/body&gt;</div>
<div>&lt;/html&gt;</div>
<div> </div>
<div> </div></div>