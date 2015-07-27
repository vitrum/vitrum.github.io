title: input高级用法 -转贴
id: 243
categories:
  - 计算机与 Internet
date: 2007-06-03 03:49:16
tags:
---

<div id="msgcns!9697D6160EFEBC17!1090" class="bvMsg"><div>最早是在经典看到的，现在被人转贴N次，已经忘记出处了</div>
<div> </div>
<div>1.取消按钮按下时的虚线框 
　　在input里添加属性值 hideFocus 或者 HideFocus=true 

2.只读文本框内容 
在input里添加属性值 readonly 

3.防止退后清空的TEXT文档(可把style内容做做为类引用) 
　　&lt;INPUT style=behavior:url(#default#savehistory); type=text id=oPersistInput&gt; 

4.ENTER键可以让光标移到下一个输入框 
　　&lt;input onkeydown=&quot;if(event.keyCode==13)event.keyCode=9&quot; &gt; 

5.只能为中文(有闪动) 
　　&lt;input onkeyup=&quot;value=value.replace(/[ -~]/g,’’)&quot; onkeydown=&quot;if(event.keyCode==13)event.keyCode=9&quot;&gt; 

6.只能为数字(有闪动) 
　　&lt;input onkeyup=&quot;value=value.replace(/[^d]/g,’’) &quot;onbeforepaste=&quot;clipboardData.setData(’text’,clipboardData.getData(’text’).replace(/[^d]/g,’’))&quot;&gt; 

7.只能为数字(无闪动) 
　　&lt;input style=&quot;ime-mode:disabled&quot; onkeydown=&quot;if(event.keyCode==13)event.keyCode=9&quot; onKeyPress=&quot;if ((event.keyCode&lt;48 || event.keyCode&gt;57)) event.returnValue=false&quot;&gt; 

8.只能输入英文和数字(有闪动) 
　　&lt;input onkeyup=&quot;value=value.replace(/[W]/g,’’)&quot; onbeforepaste=&quot;clipboardData.setData(’text’,clipboardData.getData(’text’).replace(/[^d]/g,’’))&quot;&gt; 

9.屏蔽输入法 
　　&lt;input type=&quot;text&quot; name=&quot;url&quot; style=&quot;ime-mode:disabled&quot; onkeydown=&quot;if(event.keyCode==13)event.keyCode=9&quot;&gt; 

10\. 只能输入 数字，小数点，减号（-） 字符(无闪动) 
　　&lt;input onKeyPress=&quot;if (event.keyCode!=46 &amp;&amp; event.keyCode!=45 &amp;&amp; (event.keyCode&lt;48 || event.keyCode&gt;57)) event.returnValue=false&quot;&gt; 

11\. 只能输入两位小数，三位小数(有闪动) 
　　&lt;input maxlength=9 onkeyup=&quot;if(value.match(/^d&#123;3&#125;$/))value=value.replace(value,parseInt(value/10)) ;value=value.replace(/.d*./g,’.’)&quot; onKeyPress=&quot;if((event.keyCode&lt;48 || event.keyCode&gt;57) &amp;&amp; event.keyCode!=46 &amp;&amp; event.keyCode!=45 || value.match(/^d&#123;3&#125;$/) || /.d&#123;3&#125;$/.test(value)) &#123;event.returnValue=false&#125;&quot; id=text_kfxe name=text_kfxe&gt; 

------------------------------------------------------------------------
&lt;input type=&quot;text&quot; name=&quot;input1&quot; value=&quot;中国&quot;&gt;

怎样使input中的内容为只读，也就是说不让用户更改里面的内容。
&lt;input type=&quot;text&quot; name=&quot;input1&quot; value=&quot;中国&quot; onfocus=this.blur()&gt;
&lt;input type=&quot;text&quot; name=&quot;input1&quot; value=&quot;中国&quot; readonly&gt;
&lt;input type=&quot;text&quot; name=&quot;input1&quot; value=&quot;中国&quot; disabled&gt;
最好不要用disabled,不然就无法取出里面的值了.
&lt;input type=&quot;text&quot; name=&quot;input1&quot; value=&quot;中国&quot; readonly=&quot;true&quot;&gt;
&lt;input type=&quot;text&quot; name=&quot;input1&quot; value=&quot;中国&quot; readonly style=&quot;color:#999 ;&quot;&gt; </div></div>