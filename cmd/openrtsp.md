```
shell> brew install openrtsp
```

```
shell> live555MediaServer
```

```
LIVE555 Media Server
	version 0.90 (LIVE555 Streaming Media library version 2017.05.29).
Play streams from this server using the URL
	rtsp://10.0.1.4:8554/<filename>
where <filename> is a file present in the current directory.
Each file's type is inferred from its name suffix:
	".264" => a H.264 Video Elementary Stream file
	".265" => a H.265 Video Elementary Stream file
	".aac" => an AAC Audio (ADTS format) file
	".ac3" => an AC-3 Audio file
	".amr" => an AMR Audio file
	".dv" => a DV Video file
	".m4e" => a MPEG-4 Video Elementary Stream file
	".mkv" => a Matroska audio+video+(optional)subtitles file
	".mp3" => a MPEG-1 or 2 Audio file
	".mpg" => a MPEG-1 or 2 Program Stream (audio+video) file
	".ogg" or ".ogv" or ".opus" => an Ogg audio and/or video file
	".ts" => a MPEG Transport Stream file
		(a ".tsx" index file - if present - provides server 'trick play' support)
	".vob" => a VOB (MPEG-2 video with AC-3 audio) file
	".wav" => a WAV Audio file
	".webm" => a WebM audio(Vorbis)+video(VP8) file
See http://www.live555.com/mediaServer/ for additional documentation.
(We use port 8000 for optional RTSP-over-HTTP tunneling, or for HTTP live streaming (for indexed Transport Stream files only).)
```

```
shell> wget http://www.live555.com/mediaServer/macosx/live555MediaServer
shell> chmod +x live555MediaServer
shell> ./live555MediaServer mymovie.mkv
```


```
http://www.live555.com/mediaServer/macosx/live555MediaServer
http://www.live555.com/mediaServer/linux/live555MediaServer
http://www.live555.com/mediaServer/freebsd/live555MediaServer
```

```
shell> ffplay rtsp://10.0.1.4:8554/mymovie.mkv
```

- http://www.live555.com/openRTSP
- http://www.live555.com/mediaServer/
- http://www.live555.com/liveMedia/
- http://www.live555.com/liveMedia/public/
- http://www.live555.com/proxyServer/
