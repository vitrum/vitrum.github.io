title: 'Remove webkit border on input on focus , for jQuery plugin :  jqTransform'
id: 645
categories:
  - HTML5
  - Uncategorized
date: 2011-03-17 13:53:00
tags:
---

## Examples

The following image shows a text box which is first not focussed and then focussed in the Chrome and Firefox web browsers. The highlight around the box is quite subtle in Firefox and extremely clear in Chrome; it's much more obvious in Chrome which field has the focus.
<div>![input field focus in chrome and firefox](http://www.electrictoolbox.com/images/content/chrome-firefox-input-focus.png)</div>

## Preventing the focus highlight

<pre>.noFocus:focus {
    outline: none;
}</pre>