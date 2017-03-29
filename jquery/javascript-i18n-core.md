
```
$(selector).twzipcode({
  language: 'lang/zh-tw' //不需加上 .js
});
```

```html
<head>
  <script type="text/javascript" src="i18n.js"></script>
</head>

<script>
  i18n.set({
    'lang': '"ISO639-1-ISO3166-1" language code', //e.g. en-us, zh-tw. Default is auto detect from browser.
    'path': 'language file\'s path' // Default is empty (same level as i18n.js)
  });

  var s = i18n.t('LANGUAGE ID');
  var s = i18n.datetime();
  var s = i18n.datetime('Date time');
</script>
```

#### :books: 參考網站：
- https://github.com/essoduke/javascript-i18n-core