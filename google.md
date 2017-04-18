
---

```html
<!DOCTYPE html>
<html>
  <head>
    <style type="text/css">
      html,
      body {
        height: 100%;
        margin: 0;
        padding: 0;
      }
      
      #map {
        height: 100%;
      }
    </style>
  </head>

  <body>
    <div id="map"></div>
    <script type="text/javascript">
      var map;

      function initMap() {
        map = new google.maps.Map(document.getElementById('map'), {
          center: {
            lat: -34.397,
            lng: 150.644
          },
          zoom: 8
        });
      }
    </script>
    <script async defer src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&callback=initMap">
    </script>
  </body>

</html>
```

#### :books: 參考網站：
- [Hello, World](https://developers.google.com/maps/documentation/javascript/tutorial?hl=zh-tw#The_Hello_World_of_Google_Maps_v3)

```
<iframe width="100%" height="350" frameborder="0" scrolling="no" marginheight="0" marginwidth="0" src="https://maps.google.com/maps?f=q&source=s_q&hl=zh-TW&geocode=&q=25.079264,121.482652&z=16&output=embed&t=h"></iframe>
```

#### :books: 參考網站：
- http://maps.googleapis.com/maps/api/geocode/json?address=三和路四段191巷5號&sensor=false&language=zh-TW

---

> `HAR` (`HTTP 封存`) 是多項 `HTTP` 工作階段工具用於匯出擷取資料的檔案格式。 這種格式基本上是 `JSON` 物件，且具有特定的欄位分佈。
> 「`HAR 分析工具`」可讓您檢視及瀏覽擷取的 `HAR` 檔案，並且對擷取的資料提供了一些分析。
> `Flush Google DNS` 可讓您在 `Google` 公用 `DNS` 快取 (`8.8.4.4` 和 `8.8.8.8`) 中 排清網域的 `DNS` 快取。
> `Chrome 連線診斷工具`是 `Chrome` 和 `Chrome 作業系統`專用的網路測試及疑難排解工具，既快速又簡便。


#### :books: 參考網站：
- https://toolbox.googleapps.com/apps/main/
- [Browserinfo](https://toolbox.googleapps.com/apps/browserinfo/)
- [Check MX](https://toolbox.googleapps.com/apps/checkmx/)
- [Dig](https://toolbox.googleapps.com/apps/dig/)
- [Messageheader](https://toolbox.googleapps.com/apps/messageheader/)
- [HAR 分析工具](https://toolbox.googleapps.com/apps/har_analyzer/)
- [編碼/解碼](https://toolbox.googleapps.com/apps/encode_decode/)
- [Flush Google DNS](https://google-public-dns.appspot.com/cache)

---

![](http://i.imgur.com/5oWbqTd.png)

> `Google`從`Chrome` 53版本開始便分階著手段淘汰`Flash`，在最新釋出的桌面版`Chrome` 55直接預設載入網頁為`HTML5`，除了YouTube、Facebook、Yahoo等十大網站享有`Flash`豁免權外，其他Flash網頁都必須主動啟用。

chrome://settings/

`顯示進階設定...` → ☑ `在可用時使用硬體加速`


`Chrome` 鍵盤快速鍵

**重新開啟並切換至最近關閉的分頁**	<kbd>⌘</kbd> + <kbd>Shift</kbd> + <kbd>T</kbd>
**切換至特定分頁**	     <kbd>⌘</kbd> + <kbd>1</kbd> 到 <kbd>⌘</kbd> + <kbd>8</kbd> 
**切換至最後一個分頁**      <kbd>⌘</kbd> + <kbd>9</kbd>
**切換至下一個開啟的分頁**	 <kbd>⌘</kbd> + <kbd>Option</kbd> + <kbd>→</kbd>
**切換至上一個開啟的分頁**	 <kbd>⌘</kbd> + <kbd>Option</kbd> + <kbd>←</kbd>
**將視窗縮到最小**	     <kbd>⌘</kbd> + <kbd>M</kbd>
**隱藏 Google Chrome**	<kbd>⌘</kbd> + <kbd>H</kbd>
**退出 Google Chrome**	<kbd>⌘</kbd> + <kbd>Q</kbd>
**向下捲動網頁，每次捲動一個螢幕畫面的範圍**	<kbd>空格鍵</kbd>
**向上捲動網頁，每次捲動一個螢幕畫面的範圍**	<kbd>Shift</kbd> + <kbd>空格鍵</kbd>

**放大網頁上的所有內容** <kbd>⌘</kbd> + <kbd>+</kbd>
**縮小網頁上的所有內容** <kbd>⌘</kbd> + <kbd>-</kbd>
**將網頁上的所有內容都回復為預設大小**	<kbd>⌘</kbd> + <kbd>0</kbd>


<kbd>⌘</kbd> + <kbd>↑</kbd>
<kbd>⌘</kbd> + <kbd>↓</kbd>

#### :books: 參考網站：
- [快速鍵](https://support.google.com/chrome/answer/157179?hl=zh-Hant)

---

```css
/*
 * cwTeXHei (Chinese-traditional) http://www.google.com/fonts/earlyaccess
 */

@font-face {
  font-family: 'cwTeXHei';
  font-style: normal;
  font-weight: 500;
  src: url(//fonts.gstatic.com/ea/cwtexhei/v3/cwTeXHei-zhonly.eot);
  src: url(//fonts.gstatic.com/ea/cwtexhei/v3/cwTeXHei-zhonly.eot?#iefix) format('embedded-opentype'), url(//fonts.gstatic.com/ea/cwtexhei/v3/cwTeXHei-zhonly.woff2) format('woff2'), url(//fonts.gstatic.com/ea/cwtexhei/v3/cwTeXHei-zhonly.woff) format('woff'), url(//fonts.gstatic.com/ea/cwtexhei/v3/cwTeXHei-zhonly.ttf) format('truetype');
}
```

```css
@import url(http://fonts.googleapis.com/earlyaccess/cwtexhei.css);
```
```css
font-family: 'cwTeXHei',
sans-serif;
```

#### :books: 參考網站：
- [Google Fonts](https://fonts.google.com/)
- [earlyaccess](https://fonts.google.com/earlyaccess)

---

德國時間
日本時間
美國時間
中國時間
澳洲時間
Greenwich時間
台北時間

---

Google 翻譯
```
=GOOGLETRANSLATE("", "zh-CN", "zh-TW")
=GOOGLETRANSLATE("", "ja", "")
=GOOGLETRANSLATE("", "en", "")
=GOOGLETRANSLATE("", "zh-TW", "en")
```

```
=GOOGLEFINANCE("currency:USDTWD")
```
---

#### :books: 參考網站：
- https://www.google.com/finance/converter

---

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.2.4/jquery.min.js"></script>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js"></script>

<link rel="stylesheet" href="https://ajax.googleapis.com/ajax/libs/jquerymobile/1.4.5/jquery.mobile.min.css">
<script src="https://ajax.googleapis.com/ajax/libs/jquerymobile/1.4.5/jquery.mobile.min.js"></script>

<link rel="stylesheet" href="https://ajax.googleapis.com/ajax/libs/jqueryui/1.12.1/themes/smoothness/jquery-ui.css">
<script src="https://ajax.googleapis.com/ajax/libs/jqueryui/1.12.1/jquery-ui.min.js"></script>
```

```html
<script type="text/javascript" src="https://www.google.com/jsapi"></script>

<script type="text/javascript">
  google.load("search", "1");
  google.load("jquery", "1.4.2");
  google.load("jqueryui", "1.7.2");
</script>
```

- https://jsfiddle.net/api/post/library/pure/

```html
<script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>
<div id="piechart" style="width: 900px; height: 500px;"></div>
```
```js
google.charts.load('current', {
  'packages': ['corechart']
});
google.charts.setOnLoadCallback(drawChart);

function drawChart() {
  var data = google.visualization.arrayToDataTable([
    ['Task', 'Hours per Day'],
    ['Work', 11],
    ['Eat', 2],
    ['Commute', 2],
    ['Watch TV', 2],
    ['Sleep', 7]
  ]);

  var options = {
    title: 'My Daily Activities'
  };

  var chart = new google.visualization.PieChart(document.getElementById('piechart'));

  chart.draw(data, options);
}
```

#### :books: 參考網站：
- https://developers.google.com/speed/libraries/
- https://developers.google.com/loader/
- https://developers.google.com/chart/

---

- https://jsfiddle.net/g356phw2/
- https://jsfiddle.net/91krxujv/

```html
<iframe width="1280" height="720" src="https://www.youtube.com/embed/XxJKnDLYZz4?list=PLj7CmGWxRE8RIpxvAB7iBEWz3-VcwOirm" frameborder="0" allowfullscreen></iframe>

<iframe width="1280" height="720" src="https://www.youtube.com/embed/yk2CUjbyyQY?list=PLj7CmGWxRE8RIpxvAB7iBEWz3-VcwOirm" frameborder="0" allowfullscreen></iframe>


<iframe style="height: 400px;" frameborder="0" allowfullscreen="1" title="YouTube video player" width="640" height="400" src="https://www.youtube.com/embed/qE5SMobMr9Q?autoplay=1&amp;cc_load_policy=1&amp;controls=2&amp;hl=zh-Hant&amp;rel=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fsupport.google.com&amp;widgetid=1" id="widget2"></iframe>


<iframe width="560" height="315" src=" 
https://www.youtube.com/embed/D6Ac5JpCHmI?&autoplay=1" frameborder="0" 
allowfullscreen></iframe>

<iframe allowfullscreen="" frameborder="0" height="315" src="http://www.youtube.com/embed/UkWd0azv3fQ#t=2m30s" width="420"></iframe>
```

`controls=0`
`controls=1`
`autoplay=1`
`showinfo=0`
`showinfo=1`

> 如要讓嵌入影片自動顯示字幕，請將「`&cc_load_policy=1`」加到影片內嵌程式碼中。
> 「`cc_lang_pref`」可設定影片字幕的語言。
> 「`cc_load_policy=1`」預設開啟字幕。

#### :books: 參考網站：
- https://support.google.com/youtube/answer/6172631?hl=zh-Hant
- https://support.google.com/youtube/answer/171780?hl=zh-Hant
- https://developers.google.com/youtube/player_parameters

---

`DNS_PROBE_FINISHED_NXDOMAIN`
`ERR_CONNECTION_REFUSED`
`ERR_INVALID_HTTP_RESPONSE`

---

#### :books: 參考網站：
- https://fonts.google.com/earlyaccess#Noto+Sans+TC
- https://cloud.google.com/free/docs/always-free-usage-limits