title: 'Drag image gallery  in iOS whit jQuery '
tags:
  - css3
  - ios
  - iphone
  - jquery
  - touch
id: 681
categories:
  - 计算机与 Internet
  - HTML5
  - jQuery
date: 2011-04-13 11:16:00
---

key point:

e.preventDefault();
var touch = e.originalEvent.touches[0] || e.originalEvent.changedTouches[0];

[Demo](http://www.glamour-sales.com.cn/m/t.drag)
<pre>
<pre>&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"&gt;
&lt;html xmlns="http://www.w3.org/1999/xhtml"&gt;
&lt;head&gt;
&lt;meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /&gt;
&lt;meta content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0;" name="viewport" /&gt;

&lt;title&gt;moblie test&lt;/title&gt;

&lt;script src="[http://ajax.googleapis.com/ajax/libs/jquery/1.5.1/jquery.min.js](http://ajax.googleapis.com/ajax/libs/jquery/1.5.1/jquery.min.js)" type="text/javascript" &gt;&lt;/script&gt;

&lt;style&gt;
html, body { margin: 0;   padding: 0;}
.droginfo { width:100%; height:40px; background:#ffc;line-height:18px}
.droginfo div {width:100px; float:left;}
.drogbox {background: #333377;    clear: left;    min-height: 240px;    min-width: 320px; max-width:480px;    position: relative;  overflow:hidden;  }
#moveBox {width:3200px; height:200px; position:absolute; left:0; top:20px; background:  #ddd; padding: 0;}
#moveBox .photo { width:150px; height:180px;  padding: 10px 5px; float:left;  }
&lt;/style&gt;

&lt;/head&gt;</pre>
<pre>&lt;body&gt;

&lt;div class="drogbox"&gt;
    &lt;div id="moveBox"&gt;
      &lt;img class="photo" src="[http://www.glamour-sales.com.cn/media/catalog/product/yv/s/YR0-518-00007.jpg](http://www.glamour-sales.com.cn/media/catalog/product/yv/s/YR0-518-00007.jpg)" /&gt;
      &lt;img class="photo" src="[http://www.glamour-sales.com.cn/media/catalog/product/yv/s/YR0-518-00006.jpg](http://www.glamour-sales.com.cn/media/catalog/product/yv/s/YR0-518-00006.jpg)" /&gt;
      &lt;img class="photo" src="[http://www.glamour-sales.com.cn/media/catalog/product/yv/s/YR0-518-00005.jpg](http://www.glamour-sales.com.cn/media/catalog/product/yv/s/YR0-518-00005.jpg)" /&gt;
      &lt;img class="photo" src="[http://www.glamour-sales.com.cn/media/catalog/product/yv/s/YR0-518-00004.jpg](http://www.glamour-sales.com.cn/media/catalog/product/yv/s/YR0-518-00004.jpg)" /&gt;
      &lt;img class="photo" src="[http://www.glamour-sales.com.cn/media/catalog/product/yv/s/YR0-518-00003.jpg](http://www.glamour-sales.com.cn/media/catalog/product/yv/s/YR0-518-00003.jpg)" /&gt;
      &lt;img class="photo" src="[http://www.glamour-sales.com.cn/media/catalog/product/yv/s/YR0-518-00002.jpg](http://www.glamour-sales.com.cn/media/catalog/product/yv/s/YR0-518-00002.jpg)" /&gt;</pre>
<pre>      &lt;img class="photo" src="[http://www.glamour-sales.com.cn/media/catalog/product/yv/s/YR0-518-00001.jpg](http://www.glamour-sales.com.cn/media/catalog/product/yv/s/YR0-518-00001.jpg)" /&gt;
    &lt;/div&gt;
&lt;/div&gt;

&lt;div class="droginfo"&gt;
  &lt;div&gt;pageX:&lt;span  id="movex" &gt;&lt;/span&gt;&lt;/div&gt;
  &lt;div&gt;pageY:&lt;span  id="movey" &gt;&lt;/span&gt;&lt;/div&gt;
  &lt;div&gt;changeX:&lt;span  id="changex" &gt;&lt;/span&gt;&lt;/div&gt;
  &lt;div&gt;autofix:&lt;span  id="moveend" &gt;&lt;/span&gt;&lt;/div&gt;</pre>
<pre>&lt;/div&gt;
&lt;script type="text/javascript"&gt;

var changeXOld = 0;
var changeXNew = 0;
var firstTouchX = 0;
var moveThing =  jQuery('#moveBox');
var moveList = jQuery('#moveBox img').length;

jQuery('#moveBox').width( moveList  * 160);

jQuery('.drogbox').bind('touchstart',function(e){

      var moveBoxoffset = moveThing.offset();
      e.preventDefault();
      var touch = e.originalEvent.touches[0] || e.originalEvent.changedTouches[0];

      changeXOld = moveBoxoffset .left;
      firstTouchX = touch.pageX;

}).bind('touchmove',function(e){

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
                      jQuery('#changex').text(changeXOld + "," + changeXNew );
                      jQuery('#moveend').text('');
           }
      }

      var newXpoint = (changeXOld - ( firstTouchX  - touch.pageX)) + 'px';
      jQuery('#moveBox').css("left",newXpoint);

}).bind('touchend',function(e){
      e.preventDefault();
      var touch = e.originalEvent.touches[0] || e.originalEvent.changedTouches[0];
      var moveBoxoffset = moveThing.offset();
      var maxLeft = moveThing.width();

      changeXNew = moveBoxoffset .left;

      jQuery('#changex').text(changeXOld + "," + changeXNew);

      var jumpX = jQuery('.drogbox').width();
      var drogChange = changeXNew - changeXOld ;

      if ( drogChange  &gt; 10  )  {
         var newXpoint = ( (parseInt(moveBoxoffset.left / jumpX )) * jumpX )  + 'px';
         jQuery('#moveBox').animate({left: newXpoint }, 180);
         jQuery('#moveend').text('&gt;10 +++');
      }
     if ( drogChange  &lt; -10  )  {
         var newXpoint = ( (parseInt(moveBoxoffset.left / jumpX )) * jumpX - jumpX) ;
        if ( (newXpoint* -1) &gt;= (maxLeft - jumpX) ){
             newXpoint = (maxLeft * -1) + jumpX + 'px';
         }else {     newXpoint = newXpoint  + 'px';     }

         jQuery('#moveBox').animate({left:newXpoint }, 180);
         jQuery('#moveend').text('&lt;-10 ---');
      }
     if ( drogChange  &gt;= -10 &amp;&amp; drogChange  &lt;= 10  ){
        var newXpoint = changeXOld + 'px';
        jQuery('#moveBox').animate({left:newXpoint }, 50);
     }
});

&lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;</pre>
</pre>