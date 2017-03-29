
```console
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

#### :books: 參考網站：
- https://github.com/essoduke/jQuery-TWzipcode