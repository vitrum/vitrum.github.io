title: FLASH震动窗口
id: 608
categories:
  - 计算机与 Internet
date: 2005-09-13 07:56:18
tags:
---

<div id="msgcns!9697D6160EFEBC17!189" class="bvMsg"><div>getURL(&quot;javascript:winQuake()&quot;) </div>
<div> </div>
<div>&lt;!-- 
// Seismic window by Paul Anderson, copyright 1999 CNET, Inc. 
var quakeID=0; 
var deltaX=0; 
var deltaY=0; 

function tremor(dir) &#123; // -10 to 10 
with(Math) return ceil(random()*10)*2*(floor(random()*2)-.5); 
&#125; 

function winQuake() &#123; 
clearTimeout(quakeID); 
for (i=0;i&lt;=((Math.random()*35)+5);i++) &#123; 
  xShift = tremor(); 
  yShift = tremor(); 
  window.moveBy(xShift,yShift); 
  deltaX -= xShift; 
  deltaY -= yShift; 
  &#125; 
winReset(); 
quakeID=setTimeout(&quot;winQuake()&quot;,Math.ceil(Math.random()*3500)+250); 
&#125; 

function winReset() &#123; 
window.moveBy(deltaX,deltaY); 
deltaX=0; deltaY=0; 
&#125; 

//window.onload=winQuake;隨載入啟動 
//window.onunload=winReset;//當關閉重?#93;晃動值 
//--&gt;</div></div>