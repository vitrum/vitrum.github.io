title: CSS 换肤技术
id: 629
categories:
  - Uncategorized
date: 2005-08-29 07:22:53
tags:
---

<div id="msgcns!9697D6160EFEBC17!151" class="bvMsg">

[http://cnbruce.com/test/css/](http://cnbruce.com/test/css/)

&lt;HTML&gt;
&lt;HEAD&gt;
&lt;link ID=&quot;skin&quot; rel=&quot;stylesheet&quot; type=&quot;text/css&quot;&gt;
&lt;TITLE&gt;换肤技术&lt;/TITLE&gt;
&lt;SCRIPT LANGUAGE=javascript&gt;
&lt;!--
function SetCookie(name,value)&#123;
     var argv=SetCookie.arguments;
     var argc=SetCookie.arguments.length;
     var expires=(2&lt;argc)?argv[2]:null;
     var path=(3&lt;argc)?argv[3]:null;
     var domain=(4&lt;argc)?argv[4]:null;
     var secure=(5&lt;argc)?argv[5]:false;
     document.cookie=name+&quot;=&quot;+escape(value)+((expires==null)?&quot;&quot;:(&quot;; expires=&quot;+expires.toGMTString()))+((path==null)?&quot;&quot;:(&quot;; path=&quot;+path))+((domain==null)?&quot;&quot;:(&quot;; domain=&quot;+domain))+((secure==true)?&quot;; secure&quot;:&quot;&quot;);
&#125;

function GetCookie(Name) &#123;
     var search = Name + &quot;=&quot;;
     var returnvalue = &quot;&quot;;
     if (document.cookie.length &gt; 0) &#123;
           offset = document.cookie.indexOf(search);
           if (offset != -1) &#123;      
                 offset += search.length;
                 end = document.cookie.indexOf(&quot;;&quot;, offset);                        
                 if (end == -1)
                       end = document.cookie.length;
                 returnvalue=unescape(document.cookie.substring(offset,end));
           &#125;
     &#125;
     return returnvalue;
&#125;

var thisskin;
thisskin=GetCookie(&quot;nowskin&quot;);
if(thisskin!=&quot;&quot;)
     skin.href=thisskin;
else
     skin.href=&quot;css.css&quot;;

function changecss(url)&#123;
     if(url!=&quot;&quot;)&#123;
           skin.href=url;
           var expdate=new Date();
           expdate.setTime(expdate.getTime()+(24*60*60*1000*30));
           //expdate=null;
                                   //以下设置COOKIES时间为1年,自己随便设置该时间..
           SetCookie(&quot;nowskin&quot;,url,expdate,&quot;/&quot;,null,false);
     &#125;
&#125;
//--&gt;
&lt;/SCRIPT&gt;
&lt;/HEAD&gt;
&lt;BODY&gt;

&lt;P&gt;请选择下面的下拉菜单测试换肤效果&lt;/P&gt;

<div></div></div>