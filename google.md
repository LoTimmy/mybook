
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

```
德國時間
日本時間
美國時間
中國時間
澳洲時間
Greenwich時間
台北時間
```

---

Google 翻譯
```
=GOOGLETRANSLATE("", "zh-CN", "zh-TW")
=GOOGLETRANSLATE("", "ja", "")
=GOOGLETRANSLATE("", "en", "")
=GOOGLETRANSLATE("", "zh-TW", "en")
```

```
=GOOGLEFINANCE("currency:USDBTC")
=GOOGLEFINANCE("currency:BTCUSD")
=GOOGLEFINANCE("currency:TWDBTC")
=GOOGLEFINANCE("currency:BTCTWD")
=GOOGLEFINANCE("currency:TWDUSD")
=GOOGLEFINANCE("currency:USDTWD")
```


```html
<select name="from" value="TWD">
  <option value="AED">United Arab Emirates Dirham (AED)</option>
  <option value="AFN">Afghan Afghani (AFN)</option>
  <option value="ALL">Albanian Lek (ALL)</option>
  <option value="AMD">Armenian Dram (AMD)</option>
  <option value="ANG">Netherlands Antillean Guilder (ANG)</option>
  <option value="AOA">Angolan Kwanza (AOA)</option>
  <option value="ARS">Argentine Peso (ARS)</option>
  <option value="AUD">Australian Dollar (A$)</option>
  <option value="AWG">Aruban Florin (AWG)</option>
  <option value="AZN">Azerbaijani Manat (AZN)</option>
  <option value="BAM">Bosnia-Herzegovina Convertible Mark (BAM)</option>
  <option value="BBD">Barbadian Dollar (BBD)</option>
  <option value="BDT">Bangladeshi Taka (BDT)</option>
  <option value="BGN">Bulgarian Lev (BGN)</option>
  <option value="BHD">Bahraini Dinar (BHD)</option>
  <option value="BIF">Burundian Franc (BIF)</option>
  <option value="BMD">Bermudan Dollar (BMD)</option>
  <option value="BND">Brunei Dollar (BND)</option>
  <option value="BOB">Bolivian Boliviano (BOB)</option>
  <option value="BRL">Brazilian Real (R$)</option>
  <option value="BSD">Bahamian Dollar (BSD)</option>
  <option value="BTC">Bitcoin (?)</option>
  <option value="BTN">Bhutanese Ngultrum (BTN)</option>
  <option value="BWP">Botswanan Pula (BWP)</option>
  <option value="BYN">Belarusian Ruble (BYN)</option>
  <option value="BYR">Belarusian Ruble (2000–2016) (BYR)</option>
  <option value="BZD">Belize Dollar (BZD)</option>
  <option value="CAD">Canadian Dollar (CA$)</option>
  <option value="CDF">Congolese Franc (CDF)</option>
  <option value="CHF">Swiss Franc (CHF)</option>
  <option value="CLF">Chilean Unit of Account (UF) (CLF)</option>
  <option value="CLP">Chilean Peso (CLP)</option>
  <option value="CNH">CNH (CNH)</option>
  <option value="CNY">Chinese Yuan (CN￥)</option>
  <option value="COP">Colombian Peso (COP)</option>
  <option value="CRC">Costa Rican Colon (CRC)</option>
  <option value="CUP">Cuban Peso (CUP)</option>
  <option value="CVE">Cape Verdean Escudo (CVE)</option>
  <option value="CZK">Czech Koruna (CZK)</option>
  <option value="DEM">German Mark (DEM)</option>
  <option value="DJF">Djiboutian Franc (DJF)</option>
  <option value="DKK">Danish Krone (DKK)</option>
  <option value="DOP">Dominican Peso (DOP)</option>
  <option value="DZD">Algerian Dinar (DZD)</option>
  <option value="EGP">Egyptian Pound (EGP)</option>
  <option value="ERN">Eritrean Nakfa (ERN)</option>
  <option value="ETB">Ethiopian Birr (ETB)</option>
  <option value="EUR">Euro (€)</option>
  <option value="FIM">Finnish Markka (FIM)</option>
  <option value="FJD">Fijian Dollar (FJD)</option>
  <option value="FKP">Falkland Islands Pound (FKP)</option>
  <option value="FRF">French Franc (FRF)</option>
  <option value="GBP">British Pound (￡)</option>
  <option value="GEL">Georgian Lari (GEL)</option>
  <option value="GHS">Ghanaian Cedi (GHS)</option>
  <option value="GIP">Gibraltar Pound (GIP)</option>
  <option value="GMD">Gambian Dalasi (GMD)</option>
  <option value="GNF">Guinean Franc (GNF)</option>
  <option value="GTQ">Guatemalan Quetzal (GTQ)</option>
  <option value="GYD">Guyanaese Dollar (GYD)</option>
  <option value="HKD">Hong Kong Dollar (HK$)</option>
  <option value="HNL">Honduran Lempira (HNL)</option>
  <option value="HRK">Croatian Kuna (HRK)</option>
  <option value="HTG">Haitian Gourde (HTG)</option>
  <option value="HUF">Hungarian Forint (HUF)</option>
  <option value="IDR">Indonesian Rupiah (IDR)</option>
  <option value="IEP">Irish Pound (IEP)</option>
  <option value="ILS">Israeli New Shekel (?)</option>
  <option value="INR">Indian Rupee (?)</option>
  <option value="IQD">Iraqi Dinar (IQD)</option>
  <option value="IRR">Iranian Rial (IRR)</option>
  <option value="ISK">Icelandic Krona (ISK)</option>
  <option value="ITL">Italian Lira (ITL)</option>
  <option value="JMD">Jamaican Dollar (JMD)</option>
  <option value="JOD">Jordanian Dinar (JOD)</option>
  <option value="JPY">Japanese Yen (￥)</option>
  <option value="KES">Kenyan Shilling (KES)</option>
  <option value="KGS">Kyrgystani Som (KGS)</option>
  <option value="KHR">Cambodian Riel (KHR)</option>
  <option value="KMF">Comorian Franc (KMF)</option>
  <option value="KPW">North Korean Won (KPW)</option>
  <option value="KRW">South Korean Won (?)</option>
  <option value="KWD">Kuwaiti Dinar (KWD)</option>
  <option value="KYD">Cayman Islands Dollar (KYD)</option>
  <option value="KZT">Kazakhstani Tenge (KZT)</option>
  <option value="LAK">Laotian Kip (LAK)</option>
  <option value="LBP">Lebanese Pound (LBP)</option>
  <option value="LKR">Sri Lankan Rupee (LKR)</option>
  <option value="LRD">Liberian Dollar (LRD)</option>
  <option value="LSL">Lesotho Loti (LSL)</option>
  <option value="LTL">Lithuanian Litas (LTL)</option>
  <option value="LVL">Latvian Lats (LVL)</option>
  <option value="LYD">Libyan Dinar (LYD)</option>
  <option value="MAD">Moroccan Dirham (MAD)</option>
  <option value="MDL">Moldovan Leu (MDL)</option>
  <option value="MGA">Malagasy Ariary (MGA)</option>
  <option value="MKD">Macedonian Denar (MKD)</option>
  <option value="MMK">Myanmar Kyat (MMK)</option>
  <option value="MNT">Mongolian Tugrik (MNT)</option>
  <option value="MOP">Macanese Pataca (MOP)</option>
  <option value="MRO">Mauritanian Ouguiya (MRO)</option>
  <option value="MUR">Mauritian Rupee (MUR)</option>
  <option value="MVR">Maldivian Rufiyaa (MVR)</option>
  <option value="MWK">Malawian Kwacha (MWK)</option>
  <option value="MXN">Mexican Peso (MX$)</option>
  <option value="MYR">Malaysian Ringgit (MYR)</option>
  <option value="MZN">Mozambican Metical (MZN)</option>
  <option value="NAD">Namibian Dollar (NAD)</option>
  <option value="NGN">Nigerian Naira (NGN)</option>
  <option value="NIO">Nicaraguan Cordoba (NIO)</option>
  <option value="NOK">Norwegian Krone (NOK)</option>
  <option value="NPR">Nepalese Rupee (NPR)</option>
  <option value="NZD">New Zealand Dollar (NZ$)</option>
  <option value="OMR">Omani Rial (OMR)</option>
  <option value="PAB">Panamanian Balboa (PAB)</option>
  <option value="PEN">Peruvian Sol (PEN)</option>
  <option value="PGK">Papua New Guinean Kina (PGK)</option>
  <option value="PHP">Philippine Peso (PHP)</option>
  <option value="PKG">PKG (PKG)</option>
  <option value="PKR">Pakistani Rupee (PKR)</option>
  <option value="PLN">Polish Zloty (PLN)</option>
  <option value="PYG">Paraguayan Guarani (PYG)</option>
  <option value="QAR">Qatari Rial (QAR)</option>
  <option value="RON">Romanian Leu (RON)</option>
  <option value="RSD">Serbian Dinar (RSD)</option>
  <option value="RUB">Russian Ruble (RUB)</option>
  <option value="RWF">Rwandan Franc (RWF)</option>
  <option value="SAR">Saudi Riyal (SAR)</option>
  <option value="SBD">Solomon Islands Dollar (SBD)</option>
  <option value="SCR">Seychellois Rupee (SCR)</option>
  <option value="SDG">Sudanese Pound (SDG)</option>
  <option value="SEK">Swedish Krona (SEK)</option>
  <option value="SGD">Singapore Dollar (SGD)</option>
  <option value="SHP">St. Helena Pound (SHP)</option>
  <option value="SKK">Slovak Koruna (SKK)</option>
  <option value="SLL">Sierra Leonean Leone (SLL)</option>
  <option value="SOS">Somali Shilling (SOS)</option>
  <option value="SRD">Surinamese Dollar (SRD)</option>
  <option value="STD">Sao Tome &amp; Principe Dobra (STD)</option>
  <option value="SVC">Salvadoran Colon (SVC)</option>
  <option value="SYP">Syrian Pound (SYP)</option>
  <option value="SZL">Swazi Lilangeni (SZL)</option>
  <option value="THB">Thai Baht (THB)</option>
  <option value="TJS">Tajikistani Somoni (TJS)</option>
  <option value="TMT">Turkmenistani Manat (TMT)</option>
  <option value="TND">Tunisian Dinar (TND)</option>
  <option value="TOP">Tongan Pa?anga (TOP)</option>
  <option value="TRY">Turkish Lira (TRY)</option>
  <option value="TTD">Trinidad &amp; Tobago Dollar (TTD)</option>
  <option selected="" value="TWD">New Taiwan Dollar (NT$)</option>
  <option value="TZS">Tanzanian Shilling (TZS)</option>
  <option value="UAH">Ukrainian Hryvnia (UAH)</option>
  <option value="UGX">Ugandan Shilling (UGX)</option>
  <option value="USD">US Dollar ($)</option>
  <option value="UYU">Uruguayan Peso (UYU)</option>
  <option value="UZS">Uzbekistani Som (UZS)</option>
  <option value="VEF">Venezuelan Bolivar (VEF)</option>
  <option value="VND">Vietnamese Dong (?)</option>
  <option value="VUV">Vanuatu Vatu (VUV)</option>
  <option value="WST">Samoan Tala (WST)</option>
  <option value="XAF">Central African CFA Franc (FCFA)</option>
  <option value="XCD">East Caribbean Dollar (EC$)</option>
  <option value="XDR">Special Drawing Rights (XDR)</option>
  <option value="XOF">West African CFA Franc (CFA)</option>
  <option value="XPF">CFP Franc (CFPF)</option>
  <option value="YER">Yemeni Rial (YER)</option>
  <option value="ZAR">South African Rand (ZAR)</option>
  <option value="ZMK">Zambian Kwacha (1968–2012) (ZMK)</option>
  <option value="ZMW">Zambian Kwacha (ZMW)</option>
  <option value="ZWL">Zimbabwean Dollar (2009) (ZWL)</option>
</select>
```



---

#### :books: 參考網站：
- https://www.google.com/finance/converter
- https://support.google.com/docs/table/25273?hl=zh-Hant

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