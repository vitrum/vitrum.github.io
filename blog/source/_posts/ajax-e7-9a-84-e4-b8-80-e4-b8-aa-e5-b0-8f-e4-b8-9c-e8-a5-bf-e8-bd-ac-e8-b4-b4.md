title: AJAX的一个小东西--转贴
id: 365
categories:
  - 计算机与 Internet
date: 2006-03-20 01:58:26
tags:
---

<div id="msgcns!9697D6160EFEBC17!623" class="bvMsg"><div>出处:蓝色理想</div>
<div>作者:hubro</div>
<div> </div>
<div>[<u><font color="#800080">www.hubro.net/spank.aspx</font></u>](http://www.hubro.net/spank.aspx)
还是老外写得好
用AJAX请求XML文件,返回XML再处理,生成HTML</div>
<div> </div>
<div> </div>
<div>...
xmlhttp.open(sMethod, sURL, <font color="red">true</font>); 这个true才是不卡的原因
xmlhttp.onreadystatechange = function() &#123;
if (xmlhttp.readyState == 4 &amp;&amp; !bComplete)//再才发现,为什么别人写的不卡了,原因在这,请求完成后才处理
...

顺便问问网速慢的卡不</div>
<div><pre>function ajaxObj()
&#123;
  var xmlhttp, bComplete = false;
  try &#123; xmlhttp = new ActiveXObject(&quot;Msxml2.XMLHTTP&quot;); &#125;
  catch (e) &#123; try &#123; xmlhttp = new ActiveXObject(&quot;Microsoft.XMLHTTP&quot;); &#125;
  catch (e) &#123; try &#123; xmlhttp = new XMLHttpRequest(); &#125;
  catch (e) &#123; xmlhttp = false; &#125;&#125;&#125;
  if (!xmlhttp) return null;
  this.connect = function(sURL, sMethod, fnDone)
  &#123;
    if (!xmlhttp) return false;
    bComplete = false;
    sMethod = sMethod.toUpperCase();

    try 
	&#123;
      if (sMethod == &quot;GET&quot;)
      &#123;
        xmlhttp.open(sMethod, sURL, true);
        sVars = &quot;&quot;;
      &#125;
      else
      &#123;
        xmlhttp.open(sMethod, sURL, true);
        xmlhttp.setRequestHeader(&quot;Method&quot;, &quot;POST &quot;+sURL+&quot; HTTP/1.1&quot;);
        xmlhttp.setRequestHeader(&quot;Content-Type&quot;,&quot;application/x-www-form-urlencoded&quot;);
      &#125;
      xmlhttp.onreadystatechange = function() &#123;
        if (xmlhttp.readyState == 4 &amp;&amp; !bComplete)//再才发现,为什么别人写的不卡了,原因在这,请求完成后才处理
        &#123;
          bComplete = true;
          fnDone(xmlhttp);
        &#125;&#125;;
      xmlhttp.send(sVars);
    &#125;
    catch(z) &#123; return false; &#125;
    return true;
  &#125;;
  return this;
&#125;
代码分析
<pre>var p=15;//初始每页大小
var page=1;//初始当前页
var count=0;//初始请求的总数
var q=&quot;&quot;;//是不是有查询
var all_count=0;//初始DATATABLE的总数,由XML文件的COUNT返回
var page_count=0;//初始分页数
var t_out=false;
function replaceit(str)
&#123;
	var re;
	re=/&lt;/g;
	str=str.replace(re,&quot;&amp;lt;&quot;);
	re=/&gt;/g;
	str=str.replace(re,&quot;&amp;gt;&quot;);
	return str;
&#125;

function ajaxObj()//完成一个XMLHTTP请求,并处理
&#123;
  var xmlhttp, bComplete = false;
  try &#123; xmlhttp = new ActiveXObject(&quot;Msxml2.XMLHTTP&quot;); &#125;
  catch (e) &#123; try &#123; xmlhttp = new ActiveXObject(&quot;Microsoft.XMLHTTP&quot;); &#125;
  catch (e) &#123; try &#123; xmlhttp = new XMLHttpRequest(); &#125;
  catch (e) &#123; xmlhttp = false; &#125;&#125;&#125;
  if (!xmlhttp) return null;
  this.connect = function(sURL, sMethod, fnDone)
  &#123;
    if (!xmlhttp) return false;
    bComplete = false;
    sMethod = sMethod.toUpperCase();

    try 
	&#123;
      if (sMethod == &quot;GET&quot;)
      &#123;
        xmlhttp.open(sMethod, sURL, true);
        sVars = &quot;&quot;;
      &#125;
      else
      &#123;
        xmlhttp.open(sMethod, sURL, true);
        xmlhttp.setRequestHeader(&quot;Method&quot;, &quot;POST &quot;+sURL+&quot; HTTP/1.1&quot;);
        xmlhttp.setRequestHeader(&quot;Content-Type&quot;,&quot;application/x-www-form-urlencoded&quot;);
      &#125;
      xmlhttp.onreadystatechange = function() &#123;//处理在这呢
        if (xmlhttp.readyState == 4 &amp;&amp; !bComplete)
        &#123;
          bComplete = true;
          fnDone(xmlhttp);
        &#125;&#125;;
      xmlhttp.send(sVars);
    &#125;
    catch(z) &#123; return false; &#125;
    return true;
  &#125;;
  return this;
&#125;

function http_send(url)//发出添加请求
&#123;
	var request = new ajaxObj();	
	var requestComplete = function (oXML) &#123;
		//o(&quot;spank_body&quot;).innerHTML=&quot;Loading...&quot;;
	&#125;;
	request.connect(url, &quot;POST&quot;, requestComplete);
&#125;
function xml_dom() &#123; //返回一个XML对像,没用了
	var xmldom;
	if (window.ActiveXObject)&#123;
		 xmldom = new ActiveXObject(&quot;Microsoft.XMLDOM&quot;);
	&#125; else &#123;
		if (document.implementation &amp;&amp; document.implementation.createDocument) &#123;
		 xmldom = document.implementation.createDocument(&quot;&quot;,&quot;doc&quot;,null);
		&#125;
	&#125;
	xmldom.async = false;
	xmldom.resolveExternals = false;
	xmldom.validateOnParse = false;
	xmldom.preserveWhiteSpace = true;
	return xmldom;
&#125;

function o(obj)//获取一个元素
&#123;
return document.getElementById(obj)
&#125;

function spank_it()//添加一个新记录
&#123;
var ss1=o(&quot;select&quot;).value;
var ss2=o(&quot;talk&quot;).value;
url=&quot;?inc=new&amp;s=&quot;+ss1+&quot;&amp;t=&quot;+ss2;
http_send(url);
//document.write(url)
q=&quot;&quot;;
first();
o(&quot;talk&quot;).value=&quot;&quot;;
return false;
&#125;
function settimeout()//发出对XML文件的请求
&#123;
//var objDom = xml_dom()
url=&quot;?inc=list&amp;q=&quot;+q+&quot;&amp;page=&quot; +page+&quot;&amp;p=&quot;+p+&quot;&amp;s=&quot;+Math.random();

//objDom.load(url);

var request = new ajaxObj();	
var objDom;
	var requestComplete = function (oXML) &#123;
		responsexml(oXML.responseXML);
	&#125;;
	request.connect(url, &quot;GET&quot;, requestComplete);
	//objDom(objDom)

&#125;
function responsexml(objDom)//输出XML
&#123;
	var span_td=o(&quot;spank_body&quot;);
	var items=objDom.getElementsByTagName(&quot;item&quot;);
all_count=objDom.getElementsByTagName(&quot;count&quot;).item(0).firstChild.nodeValue;
str=&quot;&lt;table width=90%  align=right border=0 align=center cellpadding=4 cellspacing=0&gt;&quot;;
for (var i=0; i&lt;items.length; i++)
	  &#123;
	  str1=items[i].childNodes[0].firstChild.nodeValue;
	  str2=items[i].childNodes[1].firstChild.nodeValue;
	  str3=items[i].childNodes[2].firstChild.nodeValue;
	  str+=&quot;&lt;tr&gt;&lt;td align=right width=120 class=sp_title&gt;&quot;+replaceit(str1)+&quot;:&lt;/td&gt;&lt;td class=sp_content&gt;&quot;+replaceit(str2)+&quot;&lt;/td&gt;&lt;/tr&gt;&quot;;

	  &#125;
	  count=items.length;
	  str+=&quot;&lt;/table&gt;&quot;;
	  span_td.innerHTML=str;
	  var pspan=o(&quot;page_span1&quot;);
	  if(all_count % p&gt;0)
	  page_count=Math.floor(all_count / p)+1;
	  else
	  page_count=all_count / p;
	  pspan.innerHTML=page_count;
&#125;
function re_load()//初始化,当搜索和分页时
&#123;
	q=&quot;&quot;;
	first();
&#125;

function set_p(value)//设置每页大小,重新初始化
&#123;
p=value;
load_spank();
&#125;
function change_pagetxt(num)//更改分页显示
&#123;
	o(&quot;page_span&quot;).innerText=num;
&#125;
/*分页,就不多说了*/
function next()
&#123;
if(count==p)
&#123;
page+=1;
load_spank();
&#125;
change_pagetxt(page);
&#125;
function last()
&#123;
if(page&gt;1)
&#123;
page-=1;
load_spank();
&#125;
change_pagetxt(page);
&#125;
function first()
&#123;
	page=1;
load_spank();
change_pagetxt(page);
&#125;

function end()
&#123;
	page=page_count;
load_spank();
change_pagetxt(page);
&#125;

function search_spank()
&#123;
	q=o(&quot;q&quot;).value;
	load_spank();
	return false;
&#125;
function load_spank()
&#123;
	t_out=false;
	o(&quot;spank_body&quot;).innerHTML=&quot;Loading...&quot;;
	settimeout();
&#125;

</pre>
关键在这里
<pre>function settimeout()
&#123;
//var objDom = xml_dom()
url=&quot;?inc=list&amp;q=&quot;+q+&quot;&amp;page=&quot; +page+&quot;&amp;p=&quot;+p+&quot;&amp;s=&quot;+Math.random();

//objDom.load(url);

var request = new ajaxObj();	
var objDom;
	var requestComplete = function (oXML) &#123;//在完成请求时执行该方法
		responsexml(oXML.responseXML);
	&#125;;
	request.connect(url, &quot;GET&quot;, requestComplete);
	//objDom(objDom)

&#125;
</pre></pre></div></div>