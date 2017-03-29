
```console
shell> bower install jquery-tinyMap
```

```
$(selector).twzipcode({
  language: 'lang/zh-tw' //不需加上 .js
});
```

```html
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
<script src="jquery.tinyMap.js"></script>

<div id="map"></div>

<script>
  $(selector).tinyMap({
    // Map center
    'center': {
      'lat': 'Lat',
      'lng': 'Lng'
    },
    // or 'center': 'lat, lng'
    // or 'center': [lat, lng]
    // or 'center': 'ADDRESS'
    // or 'center': 'N48°45.5952  E20°59.976' // WGS84 format
    'zoom': 14
  });
</script>
```

```
#map {
    width: 'MAP WIDTH';
    height: 'MAP HEIGHT';
}
```

#### :books: 參考網站：
- https://github.com/essoduke/jQuery-tinyMap