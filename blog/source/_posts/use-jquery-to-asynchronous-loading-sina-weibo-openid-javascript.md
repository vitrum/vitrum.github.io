title: Use jQuery to asynchronous loading Sina weibo OPENID javascript
id: 662
categories:
  - jQuery
date: 2011-04-07 10:47:27
tags:
---

HTML CODE
<pre>&lt;div&gt;
  &lt;a href="####" alt="新浪微博" id="openidweibolink"&gt;新浪微博&lt;/a&gt;
  &lt;form id="openidsinafrom" action="" method="post"&gt;&lt;/form&gt;
&lt;/div&gt;</pre>
javascript with jQuery
<pre>jQuery(document).ready(function(){
  var weiboUrl = "";
  jQuery('#openidweibolink').bind('click', function() {
    var ajaxUrl 	= "/openid/weibo/";  // 后台PHP页面内配置OPENID相关参数，包括KEY值、登录回调页面地址等
    var urlCheckTime = 0 ;
    if (weiboUrl =='' ){
      jQuery.ajax({ //一个Ajax过程
      type: "post",  //以post方式与后台沟通
      url :  ajaxUrl,//与此php页面沟通
      dataType:'json',//从php返回的值以 JSON方式 解释
      data:  '', //发给php的数据
      success: function(json){//如果调用php成功
        weiboUrl = json.urlAuth;
        //window.open(newUrl);
        //alert("weiboUrl:"+weiboUrl);
        jQuery('#openidsinafrom').attr("action",weiboUrl);
        jQuery('#openidsinafrom').submit();
        }
      });
    }
  });
});</pre>