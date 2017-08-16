<img src="http://videojs.com/img/logo.png" width="200">

---

`Video.js CDN`

```html
<link href="//vjs.zencdn.net/5.4.6/video-js.min.css" rel="stylesheet">
<script src="//vjs.zencdn.net/5.4.6/video.min.js"></script>
```

```html
<link href="//example.com/path/to/video-js.min.css" rel="stylesheet">
<script src="//example.com/path/to/video.min.js"></script>
<script>
  videojs.options.flash.swf = "http://example.com/path/to/video-js.swf"
</script>
```

```html
<head>
  <link href="http://vjs.zencdn.net/5.15.1/video-js.css" rel="stylesheet">

  <!-- If you'd like to support IE8 -->
  <script src="http://vjs.zencdn.net/ie8/1.1.2/videojs-ie8.min.js"></script>
</head>

<body>
  <video id="my-video" class="video-js" controls preload="auto" width="640" height="264"
  poster="MY_VIDEO_POSTER.jpg" data-setup="{}">
    <source src="MY_VIDEO.mp4" type='video/mp4'>
    <source src="MY_VIDEO.webm" type='video/webm'>
    <p class="vjs-no-js">
      To view this video please enable JavaScript, and consider upgrading to a web browser that
      <a href="http://videojs.com/html5-video-support/" target="_blank">supports HTML5 video</a>
    </p>
  </video>

  <script src="http://vjs.zencdn.net/5.15.1/video.js"></script>
</body>
```

```
shell> npm install --save video.js
shell> npm install --save-dev video.js
shell> bower install video.js
shell> bower install --save video.js
```
---

```html
<video id="example_video_1" class="video-js vjs-default-skin"
  controls preload="auto" width="640" height="264"
  poster="http://video-js.zencoder.com/oceans-clip.png"
  data-setup='{"example_option":true}'>
 <source src="http://video-js.zencoder.com/oceans-clip.mp4" type="video/mp4" />
 <source src="http://video-js.zencoder.com/oceans-clip.webm" type="video/webm" />
 <source src="http://video-js.zencoder.com/oceans-clip.ogv" type="video/ogg" />
 <p class="vjs-no-js">To view this video please enable JavaScript, and consider upgrading to a web browser that <a href="http://videojs.com/html5-video-support/" target="_blank">supports HTML5 video</a></p>
</video>
```

`vjs-big-play-centered`

```html
<video id="example_video_1" class="video-js vjs-default-skin vjs-big-play-centered"
  controls preload="auto" width="640" height="264"
  poster="http://video-js.zencoder.com/oceans-clip.png"
  data-setup='{"example_option":true}'>
  ...
</video>
```

```js
videojs("example_video_1", {}, function(){
  // Player (this) is initialized and ready.
});
```
---

```html
<video controls autoplay preload="auto" ...>
<video data-setup='{ "controls": true, "autoplay": false, "preload": "auto" }'...>
<video ... data-setup='{ "controlBar": { "muteToggle": false } }'></video>
```

```js
var player = videojs('video-id', {
  controlBar: {
    muteToggle: false
  }
});
```

```js
var myPlayer = videojs('example_video_1');

videojs("example_video_1").ready(function(){
  var myPlayer = this;

  // EXAMPLE: Start playing the video.
  
  myPlayer.currentTime(120);
  myPlayer.play();
});
```

```html
<source src="rtmp://your.streaming.provider.net/cfx/st/&mp4:path/to/video.mp4" type="rtmp/mp4">
<source src="http://your.static.provider.net/path/to/video.mp4" type="video/mp4">
<source src="http://your.static.provider.net/path/to/video.webm" type="video/webm">
```


`rtmp://dev.wowza.longtailvideo.com/vod/_definst_/sintel/640.mp4`

---

#### :books: 參考網站：
- [videojs](http://videojs.com/)
- http://docs.videojs.com/docs/guides/options.html
- http://docs.videojs.com/docs/guides/tech.html
- http://docs.videojs.com/docs/api/index.html
- http://docs.videojs.com/docs/examples/simple-embed/index.html

