title: iOS mobile 网站特殊的Meta 标签
tags:
  - html5
  - ios
  - iphone
  - mate
id: 694
categories:
  - 计算机与 Internet
  - HTML5
  - Uncategorized
date: 2011-04-24 22:59:09
---

[http://developer.apple.com/library/safari/#documentation/appleapplications/reference/SafariHTMLRef/Articles/MetaTags.html](http://developer.apple.com/library/safari/#documentation/appleapplications/reference/SafariHTMLRef/Articles/MetaTags.html)

Apple-specific `meta` tags are described here.

### apple-mobile-web-app-status-bar-style

Sets the style of the status bar for a web application.

**<strong>Syntax**</strong>

<dl><dd>
<div>
<table>
<tbody>
<tr>
<td scope="row">
<pre>&lt;meta name="apple-mobile-web-app-status-bar-style" content="black"&gt;</pre>
</td>
</tr>
</tbody>
</table>
</div>
</dd></dl>**<strong>Discussion**</strong>

<dl><dd>This meta tag has no effect unless you first specify full-screen mode as described in [“url.”](http://developer.apple.com/library/safari/documentation/appleapplications/reference/SafariHTMLRef/Articles/InputTypes.html#//apple_ref/doc/uid/TP40008055-SW5)If `content` is set to `default`, the status bar appears normal. If set to `black`, the status bar has a black background. If set to `black-translucent`, the status bar is black and translucent. If set to `default` or `black`, the web content is displayed below the status bar. If set to `black-translucent`, the web content is displayed on the entire screen, partially obscured by the status bar. The default value is `default`.

</dd></dl>**<strong>Availability**</strong>

<dl><dd>Available in iOS 2.1 and later.</dd></dl>**<strong>Support Level**</strong>

<dl><dd>Apple extension.</dd></dl>