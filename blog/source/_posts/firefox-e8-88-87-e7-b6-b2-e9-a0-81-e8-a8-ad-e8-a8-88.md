title: Firefox 與網頁設計
id: 472
categories:
  - 计算机与 Internet
date: 2005-12-12 01:52:30
tags:
---

<div id="msgcns!9697D6160EFEBC17!413" class="bvMsg"><div>
<div> </div>
<div>
<div>
<div>[](http://spaces.msn.com/mmm2005-11-01_10.54/#entry)

### [](http://jedi.org/blog/archives/cat_hack.html) 

說真的，硬派網頁設計師要是沒有 [<u><font color="#ffcc99">Firefox</font></u>](http://moztw.org/firefox/ "Mozilla Firefox 中文版") 的話，幾乎可以說是活不下去了；這不祇是因為 Firefox 對[<u><font color="#ffcc99">網頁標準</font></u>](http://www.w3.org/TR/#Recommendations "W3C Recommendations")的支援程度比 [<u><font color="#ffcc99">IE</font></u>](http://www.microsoft.com/windows/ie/default.mspx "Internet Explorer Home") 好上許多，更是因為 Firefox 上實在有[<u><font color="#ffcc99">太多太多好用的工具</font></u>](http://jedi.org/blog/archives/WebDeveloperExtensionsList.html "Extensions for Web Designers: (16)")了。

於是，在[<u><font color="#ffcc99">布丁長輩</font></u>](http://hlb.yichi.org/blog/ "hlb")的慫恿下，我整理了一些妳可能也會感興趣的 Firefox 擴充套件……
<a></a>

首先，不特別多人知道、但是其實根本就綁兜在 Firefox 裏面的，是一個叫 [<u><font color="#ffcc99">DOM Inspector</font></u>](http://www.mozilla.org/projects/inspector/) 的好東西；顧名思義，這個工具的功能就是讓妳檢視／偵察 [<u><font color="#ffcc99">DOM (Document Object Model, 文件物件模型)</font></u>](http://www.w3.org/DOM/ "W3C Document Object Model") 的。然而在多數版本的 Firefox 中，預設並不會把這個工具一併裝起來，所以安裝的時候妳得要選擇**<font color="#ffff00">自訂安裝</font>**：
![安裝 Firefox 時選擇自訂安裝，不要使用標準安裝](http://jedi.org/blog/archives/DOM_Inspector_01.png)
然後確保「**<font color="#ffff00">開發者工具</font>**」有納入安裝項目中，這麼一來妳的 Firefox 就會具備 DOM Inspector 的功能了。
![在自訂安裝中，選取「開發者工具」](http://jedi.org/blog/archives/DOM_Inspector_02.png)

![從「工具」選單裏選取 DOM Inspector](http://jedi.org/blog/archives/DOM_Inspector_03.png)這個 DOM Inspector 可以怎麼用呢？很簡單，首先從 Firefox 的「工具」選單裏選取 DOM Inspector ，然後就會看到這樣的視窗：
![DOM Inspector 的視窗](http://jedi.org/blog/archives/DOM_Inspector_04.png)
在這個視窗中，妳可以看到整個網頁的文件物件模型架構，妳可以點選任何節點，得知其屬性值；另外，妳也可以點選圖中左上角的圖示，然後再用滑鼠游標點選網頁上的某個地方， DOM Inspector 就會告訴妳那個地方是文件中的那個節點，非常好用。除此之外， DOM Inspector 也可以用來取得 CSS 資訊及 JavaScript 資訊，算是一開始學習網頁設計時，不可或缺的良伴。

![從「工具」選單裏啟動 Aardvark](http://jedi.org/blog/archives/Aardvark_01.png)接下來我要介紹的擴充套件叫 [<u><font color="#ffcc99">Aardvark</font></u>](http://karmatics.com/aardvark/) ，這個套件目前釋出到 1.1 版。它的功能很有趣，不但可以讓妳得知特定物件的 id 或 class ，還可以讓妳進行一些「調整」。要使用這個擴充套件，首先要從「工具」選單裏選「 Start Aardvark 」，接下來當妳把滑鼠游標移到網頁組件上時，就會如圖出現相關資訊的說明：
![Aardvark 顯示的資訊：範圍、組件、 class 或 id](http://jedi.org/blog/archives/Aardvark_02.png)
Aardvark 會用紅色框框標示出該組件的範圍，並在框框左下角以小標籤顯示該組件為何、其 class 或 id 又為何。這個時候透過鍵盤操作，還可以有一些額外的功能： `<font color="#9999cc">W</font>` 可以讓該組件的範圍變寬而 `<font color="#9999cc">N</font>` 則是變窄， `<font color="#9999cc">Q</font>` 是離開 Aardvark 而 `<font color="#9999cc">U</font>` 是還原最後一次操作， `<font color="#9999cc">R</font>` 是刪除所選的組件而 `<font color="#9999cc">I</font>` 則是刪除所有環繞著所選組件的其他組件然後 `<font color="#9999cc">E</font>` 會刪除該組件的內容， `<font color="#9999cc">B</font>` 是把組件內一律設為白底黑字而 `<font color="#9999cc">C</font>` 都是隨機設定組件的底色， `<font color="#9999cc">V</font>` 是檢視所選組件的原始碼，然後 `<font color="#9999cc">D</font>` 則是移除任何該組件的固定寬度值。

接下來要介紹的是一個小工具，叫 [<u><font color="#ffcc99">ColorZilla</font></u>](http://www.iosart.com/firefox/colorzilla/ "ColorZilla Extension for Firefox and Mozilla") ，目前釋出到 0.8.3.1 版。這個工具用起來很簡單，首先用滑鼠在 Firefox 畫面左下角的滴管圖示上點一下：
![滴管圖示](http://jedi.org/blog/archives/ColorZilla_01.png)
這時候滑鼠游標就會變成十字形（準星），然後當妳把滑鼠游標移動到任何地方時， ColorZilla 就會顯示出游標所在位置的色彩資訊（包括 RGB HEX 值以及顏色代碼等）：
![ColorZilla 顯示著色彩資訊](http://jedi.org/blog/archives/ColorZilla_02.png)
（補充說明一下，布丁長輩要求提示說，各位不妨在那個滴管圖示上按個滑鼠右鍵，會發現很多東西喔……）

再來要介紹的是 [<u><font color="#ffcc99">Document Map</font></u>](http://www-xray.ast.cam.ac.uk/~jgraham/mozilla.xml) ，目前釋出到 0.4 版，功能是藉由網頁內的標題組件（也就是 `<font color="#9999cc">h1</font>`, `<font color="#9999cc">h2</font>`, `<font color="#9999cc">h3</font>`, `<font color="#9999cc">h4</font>`, `<font color="#9999cc">h5</font>` 等），來建立所謂的「文件地圖」。因此，當妳想要檢視自己做出來的網站是否結構清楚、層次分明，就不能錯過這個擴充套件。使用 Document Map 的時候，要先從檢視選單裏叫出 Document Map 這個資訊方塊列：
![使用 Document Map 資訊方塊列](http://jedi.org/blog/archives/Document_Map_01.png)
然後在左方的資訊方塊列中，就會按照網頁的結構層次，把所有的標題組件列出來。這個時候，如果妳用滑鼠點一下被列出來的標題組件，瀏覽視窗中的位置也會跟著跳過去：
![](http://jedi.org/blog/archives/Document_Map_02.png)

再來要說的是 [<u><font color="#ffcc99">Fangs</font></u>](http://www.standards-schmandards.com/index.php?show/fangs) ，目前釋出到 0.9.4 版，功能是把網頁模擬成純文字瀏覽器所會看到的樣子，所以當妳特別專注於[<u><font color="#ffcc99">網頁親和力</font></u>](http://jedi.org/blog/archives/004569.html "真正的無遠弗屆 ── 談網頁內容的親和力 | Jedi")的話，這個工具可能會有些幫助。

緊接著的是一個很殘酷的擴充套件，叫 [<u><font color="#ffcc99">HTML Validator</font></u>](http://users.skynet.be/mgueury/mozilla/ "Html Validator") ，目前釋出至 0.7.6 版。怎麼說殘酷呢？因為這個擴充套件會隨時檢驗目前網頁是否為有效的 HTML ，並且以圖示顯示驗證結果：
![HTML Validator 的驗證結果](http://jedi.org/blog/archives/HTML_Validator_01.png)
這時如果把滑鼠游標移到驗證結果圖示上，還會顯示更詳細的數據：
![HTML Validator 的詳細驗證結果](http://jedi.org/blog/archives/HTML_Validator_02.png)
所以啦，任何有瑕疵的網頁，當下就會被抓包，沒有逃過的機會。

當然不是祇有這樣子而已。 HTML Validator 除了驗證 HTML 之外，也能做一點簡單的親和力驗證，而且由於這個擴充套件係根據 HTML Tidy (HTML 美容程式) 所寫成的，所以它還兼具了幫妳替網頁原始檔「整型美容」的功效，實在是好用啊！

再來是 [<u><font color="#ffcc99">linkToolbar</font></u>](http://cdn.mozdev.org/linkToolbar/) ，這個擴充套件目前釋出到 1.1.0.1 版，功能是協助導覽。大致上他會去看網頁裏面的 `<font color="#9999cc">link</font>` 詮釋資料，然後就可以讓看網頁的妳很方便地移動到網站最上層、上一層、第一篇、前一篇、後一篇、最後一篇的頁面，以及其他相關頁面（例如聯絡作者、授權資訊、其他版本……等等），由此妳也可以用來檢視妳所寫的網頁是否也提供了這些資訊，以增進親和力：
![導覽工具列](http://jedi.org/blog/archives/linkToolbar_01.png)
要特別說明的是，本來安裝了這個擴充套件後，這些導覽按鈕會自動地出現在 Firefox 的右下角，可是現在不知道為什麼，他們不會出現了，所以妳得自己從「檢視」「工具列」「自訂」把這些按鈕放到工具列上。

接下來這個擴充套件比較工程師導向，叫 [<u><font color="#ffcc99">Live HTTP Headers</font></u>](http://livehttpheaders.mozdev.org/) ，功能是直接監視伺服器傳來的 HTTP 標頭。因為有的時候，網頁設計師們會遭遇無法解決的奇怪問題，例如明明指定了語言為中文，可是頁面總是被當作英文開啟，許多這種問題，其實都來自於伺服器沒有正確組態所致，而這個擴充套件正可以幫助妳釐清這種冤屈。

下一個要介紹的擴充套件可以說是 ColorZilla 的遠親，叫 [<u><font color="#ffcc99">MeasureIt</font></u>](http://www.kevinfreitas.net/extensions/measureit/ "MeasureIt - Firefox ruler extension for web developers") ，目前釋出到 0.3.5 版，其功能顧名思義就是度量螢幕上各種東西的長度。在使用上也跟 ColorZilla 很像，首先就是以滑鼠點一下左下角的尺標圖示：
![尺標圖示](http://jedi.org/blog/archives/MeasureIt_01.png)
這時候網頁的色彩會變淡，彷彿蓋上了一層薄紗，然後妳可以用滑鼠任意畫出方框，而這個擴充套件則會告訴你這個方框的長度與寬度：
![](http://jedi.org/blog/archives/MeasureIt_02.png)
當妳得要[<u><font color="#ffcc99">錙銖必較地調整各種尺寸</font></u>](http://jedi.org/blog/archives/002703.html "我的網頁哲學 | Jedi")時，就會明白這個擴充套件有多重要了。

然後要講的是 [<u><font color="#ffcc99">mozCC</font></u>](http://yergler.net/projects/mozcc/ "mozCC") 這個擴充套件。如果妳跟我一樣還在用 Firefox 1.0.7 的話，請裝 1.1.0 版；如果妳已經換到 Firefox 1.5 的話，請裝 1.1.4 版。這個擴充套件的功能很單純：就是辨識並顯示出網頁裏的[<u><font color="#ffcc99">創用 CC</font></u>](http://creativecommons.org.tw/ "Creative Commons Taiwan") 授權資訊，所以妳可以知道自己有沒有弄錯。當網頁內嵌有創用 CC 授權資訊的詮釋資料時， Firefox 的右下角就會出現相對應的創用 CC 授權條款圖示：
![創用 CC 授權圖示](http://jedi.org/blog/archives/mozCC_01.png)
這時如果妳用滑鼠點擊這個圖示，就會出現一個視窗，告訴妳更多細節：
![mozCC 的詳細結果](http://jedi.org/blog/archives/mozCC_02.png)

緊接著又是個噁心巴拉的擴充套件，叫 [<u><font color="#ffcc99">Platypus</font></u>](http://platypus.mozdev.org/) ，目前釋出至 0.51 版，這個擴充套件會動態地建立 [<u><font color="#ffcc99">greasemonkey</font></u>](http://greasemonkey.mozdev.org/) 腳本，讓妳可以用「所見即所得」的方式，編輯任何妳看到的網頁！
![Platypus 的工具列](http://jedi.org/blog/archives/Platypus_01.png)

如果妳是多語系網頁的設計人員，那麼妳不能錯過這個 [<u><font color="#ffcc99">Quick Locale Switcher</font></u>](http://www.captaincaveman.nl/) 擴充套件。這個擴充套件目前釋出至 1.25 版，功能就是迅速切換欲索取網頁的「語系」，所以妳可以藉此檢查伺服器的運作是否正常、各種不同語言版本的網頁又是否運行如意。除了這個擴充套件外，目前釋出至 1.3.2005092701 版的 [<u><font color="#ffcc99">Popup ALT Attributes</font></u>](http://piro.sakura.ne.jp/xul/_popupalt.html.en) 和 1.4.2005110501 版的 [<u><font color="#ffcc99">XHTML Ruby Support</font></u>](http://piro.sakura.ne.jp/xul/_rubysupport.html.en) 擴充套件，也是增進 Firefox 支援的好朋友，不容錯過。

上面列了這麼多輔助工具，但是硬派網頁設計師一定不會放過網頁原始碼。因此接下來要介紹的兩個擴充套件，就都跟網頁原始碼有關。首先是 [<u><font color="#ffcc99">View formatted source</font></u>](https://addons.mozilla.org/extensions/moreinfo.php?id=697) ，這個擴充套件目前釋出至 0.9.3.4 版，利用這個擴充套件來檢視網頁原始碼時，可以看到被整理得相當整齊的結果：
![](http://jedi.org/blog/archives/View_formatted_source_01.png)
這個源碼檢視不但會把連結的其他檔案（例如 JavaScript 和 CSS 等）給放進來，而且也可以把成對的標籤「折疊」起來，非常方便。至於另一個擴充套件則叫 [<u><font color="#ffcc99">View Rendered Source Chart</font></u>](http://jennifermadden.com/scripts/ViewRenderedSource.html) ，目前釋出了免費的 1.2.03 版以及售價 1 美元的 1.3 版。這擴充套件所呈現出來的網頁原始碼，則是用不同顏色的方框，標示出原始碼的結構關係：
![View Rendered Source Chart 所呈現的原始碼](http://jedi.org/blog/archives/View_Rendered_Source_Chart_01.png)

最後，別忘了還有老字號的 [<u><font color="#ffcc99">Web Developer</font></u>](http://chrispederick.com/work/webdeveloper/) 擴充套件，他目前推出到第 0.9.4 版，具有各式各樣強力的功能，所以別忘了無論如何裝起來吧！
![Web Developer 的工具列](http://jedi.org/blog/archives/Web_Developer_01.png)

以上這些祇是我自己有安裝、而且跟網頁設計有關的 Firefox 擴充套件；因為我自己目前還在用 Firefox 1.0.7 ,所以一些描述甚麼的或許會跟在用 Firefox 1.5 的人相左，就請多運用各位自己的頭腦吧！當然，如果妳發現了甚麼好用的延伸套件，卻又不在我的列表上的，也請讓我知道吧，謝謝！
</div></div></div></div></div>