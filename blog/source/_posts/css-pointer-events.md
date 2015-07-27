title: 'CSS pointer-events '
id: 653
categories:
  - HTML5
  - Uncategorized
date: 2011-03-17 14:01:42
tags:
---

Firefox 3.6+,Safari 4,Google Chrome support Pointer-events

&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
&lt;head&gt;
&lt;meta charset="utf-8"&gt;
&lt;title&gt;CSS pointer events&lt;/title&gt;
&lt;style&gt;
.container {
position: relative;
width: 370px;
font: 15px Verdana, sans-serif;
margin: 10px auto;
}

.overlay {
position: absolute;
right: 0px;
top: 0;
width: 40px;
height: 40px;
background: rgba(0, 0, 0, 0.5);
}
.pointer-events-none {
pointer-events: none;
}
&lt;/style&gt;
&lt;script&gt;
window.onload = function () {
document.getElementById("enable-disable-pointer-events").onclick = function () {
document.getElementById("overlay").className = "overlay " + ((this.checked)? "pointer-events-none" : "");
};
};
&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;div&gt;
&lt;a href="http://twitter.com"&gt;Twitter&lt;/a&gt;, &lt;a href="http://twitter.com"&gt;Twitter&lt;/a&gt;, &lt;a href="http://twitter.com"&gt;Twitter&lt;/a&gt;, &lt;a href="http://twitter.com"&gt;Twitter&lt;/a&gt;, &lt;a href="http://twitter.com"&gt;Twitter&lt;/a&gt;, &lt;a href="http://twitter.com"&gt;Twitter&lt;/a&gt;, &lt;a href="http://twitter.com"&gt;Twitter&lt;/a&gt;, &lt;a href="http://twitter.com"&gt;Twitter&lt;/a&gt;, &lt;a href="http://twitter.com"&gt;Twitter&lt;/a&gt;, &lt;a href="http://twitter.com"&gt;Twitter&lt;/a&gt;, &lt;a href="http://twitter.com"&gt;Twitter&lt;/a&gt;, &lt;a href="http://twitter.com"&gt;Twitter&lt;/a&gt;, &lt;a href="http://twitter.com"&gt;Twitter&lt;/a&gt;, &lt;a href="http://twitter.com"&gt;Twitter&lt;/a&gt;,
&lt;div id="overlay"&gt;&lt;/div&gt;
&lt;p&gt;
&lt;input id="enable-disable-pointer-events" type="checkbox"&gt;
&lt;label for="enable-disable-pointer-events"&gt;Disable pointer events for grey box&lt;/label&gt;
&lt;/p&gt;
&lt;/div&gt;
&lt;/body&gt;
&lt;/html&gt;