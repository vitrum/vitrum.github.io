title: 原创-给sxna加上FAQ
id: 456
categories:
  - 计算机与 Internet
date: 2005-12-19 01:26:17
tags:
---

<div id="msgcns!9697D6160EFEBC17!438" class="bvMsg"><div>[SXNA](http://www.sxna.cn/f)</div>
<div> </div>
<div>第一步
======================
======================
======================
文件
INCLUDEfunction_default.asp
中,第112行加上
 Case &quot;Faq&quot;
 Export=Export_Faq()</div>
<div>第372行加上</div>
<div>Function Export_Faq()
        If not isempty(Application(SessionStr&amp;&quot;Template_Faq&quot;)) then       
  Application.Lock
  Export_Faq2=Application(SessionStr&amp;&quot;Template_Faq&quot;)
  Application.UnLock
  Else
  Export_Faq2=ReadfileByStream(&quot;TEMPLATE/&quot;&amp;TFolder&amp;&quot;/faq.html&quot;)  
  Application.Lock
  Application(SessionStr&amp;&quot;Template_Faq&quot;)=Export_Faq2
  Application.UnLock
  End If
  Export_Faq=Export_Faq2
End Function</div>
<div>第二步
======================
======================
======================
文件default.asp</div>
<div>第43行加上
&lt;A HREF=&quot;default.asp?action=Faq&quot;&gt;问&amp;答&lt;/A&gt;</div>
<div>第三步
======================
======================
======================
在TEMPLATE所选的皮肤目录中
新建一个文件&quot;faq.html&quot;
里面写上自己的F&amp;Q就可以了</div></div>