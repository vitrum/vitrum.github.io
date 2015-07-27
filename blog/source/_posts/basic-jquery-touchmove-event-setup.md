title: Basic jQuery touchmove Event Setup
tags:
  - ios
  - iphone
  - jquery
  - touch
id: 675
categories:
  - HTML5
  - jQuery
date: 2011-04-10 23:39:54
---

link:  http://www.devinrolsen.com/basic-jquery-touchmove-event-setup/
<pre><span style="font-family:Georgia, 'Times New Roman', 'Bitstream Charter', Times, serif;font-size:x-small;"><span style="line-height:19px;white-space:normal;">
</span></span>&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"&gt;&lt;html xmlns="http://www.w3.org/1999/xhtml"&gt;&lt;head&gt;&lt;meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /&gt;&lt;meta name="viewport" content="width=device-width, user-scalable=no"&gt; &lt;title&gt;Untitled Document&lt;/title&gt;&lt;script src="http://ajax.googleapis.com/ajax/libs/jquery/1.5.1/jquery.min.js" type="text/javascript" &gt;&lt;/script&gt;&lt;style&gt;.droginfo { width:110px; height:20px; background:#00C;}#someElm {width:110px; height:180px; background:#0bC; position:absolute; top:30px;}
&lt;/style&gt;&lt;/head&gt;
&lt;body&gt;&lt;div id="movex"&gt;&lt;/div&gt;&lt;div id="movey"&gt;&lt;/div&gt;

 &lt;div id="someElm"&gt;    someElm    &lt;/div&gt;

&lt;script type="text/javascript"&gt;
 jQuery('#someElm').bind('touchmove',function(e){
	      e.preventDefault();
      var touch = e.originalEvent.touches[0] || e.originalEvent.changedTouches[0]; 
     var elm = jQuery(this).offset();
      var x = touch.pageX - elm.left;
      var y = touch.pageY - elm.top;
      if(x &lt; jQuery(this).width() &amp;&amp; x &gt; 0){
	      if(y &lt; jQuery(this).height() &amp;&amp; y &gt; 0){
                  //CODE GOES HERE
                  //console.log(touch.pageY+' '+touch.pageX);
				  jQuery('#movex').text(touch.pageX);
				  jQuery('#movey').text(touch.pageY);
				  	      } 
     }});

&lt;/script&gt;&lt;/body&gt;&lt;/html&gt;</pre>