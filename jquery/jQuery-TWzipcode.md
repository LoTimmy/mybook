
```
shell> bower install jquery-TWzipcode
```

```
$(selector).twzipcode({
  language: 'lang/zh-tw' //不需加上 .js
});
```

```html
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
<script src="jquery.twzipcode.min.js"></script>

<div id="twzipcode"></div>

<div id="twzipcode">
  <div data-role="county" data-style="Style Name" data-value="110"></div>
  <div data-role="district" data-style="Style Name" data-value="臺北市"></div>
  <div data-role="zipcode" data-style="Style Name" data-value="信義區"></div>
</div>

<script>
  $('#twzipcode').twzipcode();
</script>
```

```js
$('#twzipcode').twzipcode({
  'detect': true, // 預設值為 false
  'css': ['county', 'district', 'zipcode'],
  'zipcodeSel': '106', // 此參數會優先於 countySel, districtSel
  'countySel': '臺北市',
  'districtSel': '大安區',
  'hideCounty': ['臺北市', '宜蘭縣'],
  'hideDistrict': ['三重區', '110']
});
```

```css
.zipcode {
  background-color: #c00;
  color: #fff;
}

.county {
  background-color: #4169E1;
  color: #fff;
}

.district {
  background-color: #008000;
  color: #fff;
}
```

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
  </head>

  <body>
    <div id="twzipcode"></div>
  </body>
  <script src="/bower_components/jquery/dist/jquery.min.js"></script>
  <script src="/bower_components/jquery-TWzipcode/jquery.twzipcode.min.js"></script>
  <script>
    $('#twzipcode').twzipcode();
  </script>
</html>
```

#### :books: 參考網站：
- https://github.com/essoduke/jQuery-TWzipcode
