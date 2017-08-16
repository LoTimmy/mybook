
```
shell> bower install jquery-tinyMap
```

```html
<!DOCTYPE html>
<html lang="en">

  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
      .map {
        width: 640px;
        height: 480px;
      }
      
      .labels {
        background-color: rgba(0, 0, 0, 0.5);
        border-radius: 4px;
        color: white;
        padding: 4px
      }
    </style>
  </head>

  <body>
    <div class="map"></div>
  </body>
  <script src="/bower_components/jquery/dist/jquery.min.js"></script>
  <script src="/bower_components/jquery-tinyMap/jquery.tinyMap.min.js"></script>
  <script>
    $('.map').tinyMap({
      'center': '台北市信義區台北101',
      'zoom': 14,
      'marker': [{
        'addr': ['25.0383270525352', '121.57045841217041'],
        'text': '<strong>110台灣台北市信義區松高路68號</strong>'
      }, {
        'addr': ['25.034516521123315', '121.56496524810791'],
        'text': '<strong>110台灣台北市信義區台北101</strong>'
      }, {
        'addr': ['25.039726809855434', '121.55633926391602'],
        'text': '<strong>106台灣台北市大安區光復南路280巷25號</strong>'
      }, {
        'addr': ['25.037160575899154', '121.55350685119629'],
        'text': '<strong>106台灣台北市大安區仁愛路四段300巷11號</strong>'
      }, {
        'addr': ['25.035877438787317', '121.55715465545654'],
        'text': '<strong>106台灣台北市大安區光復南路440-1號</strong>'
      }, {
        'addr': ['25.033972149830436', '121.56063079833984'],
        'text': '<strong>110台灣台北市信義區莊敬路</strong>'
      }, ],
    });
  </script>
</html>
```

```js
var map = $('#map-marker-geolocation');
map.tinyMap({
  'center': ['25.034516521123315', '121.56496524810791'],
  'zoom': 14,
  'autoLocation': function(loc) {
    map.tinyMap('modify', {
      'marker': [{
        'addr': [
          loc.coords.latitude,
          loc.coords.longitude
        ]
      }]
    });
  }
});
```

#### :books: 參考網站：
- https://github.com/essoduke/jQuery-tinyMap
