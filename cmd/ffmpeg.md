<img src="http://i.imgur.com/wHflkR8.png" width="200">

`ffmpeg - Tools for transcoding, streaming and playing of multimedia files`

### 安裝 {#installing}
```console
shell> sudo apt-get install ffmpeg
```


```console
shell> ffmpeg -i input.mpg output.mp4
```

---


```console
shell> ffmpeg -i input.mp4 -target ntsc-dvd output.mp4
```
---

```console
shell> ffmpeg -i input.mp4 -ss 0 -t 10 output.mp4
shell> ffmpeg -i input.mp4 -ss 00:05:00 -t 00:55:00 output.mp4
```
---

`ffmpeg2theora`
`ffmpeg`

```console
shell> ffplay file.mov
shell> ffplay rtmp://148.72.245.43:1935/mytv/live
```

```console
shell> ffprobe -show_format -show_streams -print_format json foo.mov
```

```
ffmpeg version 2.8.10-0ubuntu0.16.04.1 Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.4) 20160609
  configuration: --prefix=/usr --extra-version=0ubuntu0.16.04.1 --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --cc=cc --cxx=g++ --enable-gpl --enable-shared --disable-stripping --disable-decoder=libopenjpeg --disable-decoder=libschroedinger --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-librtmp --enable-libschroedinger --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzvbi --enable-openal --enable-opengl --enable-x11grab --enable-libdc1394 --enable-libiec61883 --enable-libzmq --enable-frei0r --enable-libx264 --enable-libopencv
  libavutil      54. 31.100 / 54. 31.100
  libavcodec     56. 60.100 / 56. 60.100
  libavformat    56. 40.101 / 56. 40.101
  libavdevice    56.  4.100 / 56.  4.100
  libavfilter     5. 40.101 /  5. 40.101
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  2.101 /  1.  2.101
  libpostproc    53.  3.100 / 53.  3.100
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

Getting help:
    -h      -- print basic options
    -h long -- print more options
    -h full -- print all options (including all format and codec specific options, very long)
    See man ffmpeg for detailed description of the options.

Print help / information / capabilities:
-L                  show license
-h topic            show help
-? topic            show help
-help topic         show help
--help topic        show help
-version            show version
-buildconf          show build configuration
-formats            show available formats
-devices            show available devices
-codecs             show available codecs
-decoders           show available decoders
-encoders           show available encoders
-bsfs               show available bit stream filters
-protocols          show available protocols
-filters            show available filters
-pix_fmts           show available pixel formats
-layouts            show standard channel layouts
-sample_fmts        show available audio sample formats
-colors             show available color names
-sources device     list sources of the input device
-sinks device       list sinks of the output device
-hwaccels           show available HW acceleration methods

Global options (affect whole program instead of just one file:
-loglevel loglevel  set logging level
-v loglevel         set logging level
-report             generate a report
-max_alloc bytes    set maximum size of a single allocated block
-y                  overwrite output files
-n                  never overwrite output files
-ignore_unknown     Ignore unknown stream types
-stats              print progress report during encoding
-max_error_rate ratio of errors (0.0: no errors, 1.0: 100% error  maximum error rate
-bits_per_raw_sample number  set the number of bits per raw sample
-vol volume         change audio volume (256=normal)

Per-file main options:
-f fmt              force format
-c codec            codec name
-codec codec        codec name
-pre preset         preset name
-map_metadata outfile[,metadata]:infile[,metadata]  set metadata information of outfile from infile
-t duration         record or transcode "duration" seconds of audio/video
-to time_stop       record or transcode stop time
-fs limit_size      set the limit file size in bytes
-ss time_off        set the start time offset
-sseof time_off     set the start time offset relative to EOF
-seek_timestamp     enable/disable seeking by timestamp with -ss
-timestamp time     set the recording timestamp ('now' to set the current time)
-metadata string=string  add metadata
-target type        specify target file type ("vcd", "svcd", "dvd", "dv" or "dv50" with optional prefixes "pal-", "ntsc-" or "film-")
-apad               audio pad
-frames number      set the number of frames to output
-filter filter_graph  set stream filtergraph
-filter_script filename  read stream filtergraph description from a file
-reinit_filter      reinit filtergraph on input parameter changes
-discard            discard
-disposition        disposition

Video options:
-vframes number     set the number of video frames to output
-r rate             set frame rate (Hz value, fraction or abbreviation)
-s size             set frame size (WxH or abbreviation)
-aspect aspect      set aspect ratio (4:3, 16:9 or 1.3333, 1.7777)
-bits_per_raw_sample number  set the number of bits per raw sample
-vn                 disable video
-vcodec codec       force video codec ('copy' to copy stream)
-timecode hh:mm:ss[:;.]ff  set initial TimeCode value.
-pass n             select the pass number (1 to 3)
-vf filter_graph    set video filters
-ab bitrate         audio bitrate (please use -b:a)
-b bitrate          video bitrate (please use -b:v)
-dn                 disable data

Audio options:
-aframes number     set the number of audio frames to output
-aq quality         set audio quality (codec-specific)
-ar rate            set audio sampling rate (in Hz)
-ac channels        set number of audio channels
-an                 disable audio
-acodec codec       force audio codec ('copy' to copy stream)
-vol volume         change audio volume (256=normal)
-af filter_graph    set audio filters

Subtitle options:
-s size             set frame size (WxH or abbreviation)
-sn                 disable subtitle
-scodec codec       force subtitle codec ('copy' to copy stream)
-stag fourcc/tag    force subtitle tag/fourcc
-fix_sub_duration   fix subtitles duration
-canvas_size size   set canvas size (WxH or abbreviation)
-spre preset        set the subtitle options to the indicated preset
```

---

```console
shell> ffmpeg -i input.flac -acodec libmp3lame out.mp3
shell> find . -name "*.flac" -exec bash -c 'ffmpeg -i "{}" -y "${0/.flac}.wav"' {} \;

shell> ffmpeg -i video1.webm -vf "scale=400:-1,fps=10" out.gif
shell> ffmpeg -i input.gif -c:v libvpx -auto-alt-ref 0 out.webm     
```

```console
shell> ffmpeg -i input.mp4 -ss 00:00:00 -vframes 1 img.png
shell> ffmpeg -i input.mp4 -vf fps=1/60 img-%03d.png
```

---

```console
shell> ffmpeg -codecs
shell> ffmpeg -protocols 
shell> ffmpeg -i input.mp4 output.avi
shell> ffmpeg -i input.avi -r 24 output.avi
shell> ffmpeg -i input.avi -b:v 64k -bufsize 64k output.avi

shell> ffmpeg -f avfoundation -list_devices true -i ""
shell> ffmpeg -f avfoundation -i "0:0" out.avi
shell> ffmpeg -f avfoundation -pixel_format bgr0 -i "default:none" out.avi

shell> ffmpeg -f avfoundation -i "1" -vcodec libx264 -preset ultrafast -f flv rtmp://148.72.245.43:1935/mytv/live

shell> ffmpeg -re -i input.mp4 -c copy -f flv rtmp://148.72.245.43:1935/mytv/live
shell> ffmpeg -re -i input.mp4 -c copy -vcodec libx264 -f flv rtmp://148.72.245.43:1935/mytv/live
shell> ffmpeg -i rtmp://myserver/vod/sample -c copy output.flv

shell> ffmpeg -f avfoundation -video_size 1280x720 -framerate 30 -i "0" -vcodec libx264 -preset ultrafast -pixel_format yuyv422 -f flv rtmp://148.72.245.43:1935/mytv/live

shell> ffmpeg -f avfoundation -framerate 30 -i "1:0" \
> -f avfoundation -framerate 30 -video_size 1280x720 -i "0" \
> -vcodec libx264 -preset ultrafast \
> -filter_complex overlay=x=W-w-10:y=H-h-10 \
> -acodec libmp3lame -ac 1 -ar 44100 \
> -f flv rtmp://148.72.245.43:1935/mytv/live   
```

```console
shell> ffmpeg -i input.mp4 -filter_complex subtitles=sub.srt output.mp4
shell> ffmpeg -i input.mp4 -filter_complex subtitles=filename=sub.srt output.mp4
shell> ffmpeg -i input.mp4 -filter_complex subtitles=sub.srt:force_style='FontName=DejaVu Serif,PrimaryColour=&HAA00FF00' output.mp4
```

```console
shell> ffmpeg -i input.mp4 -vf scale=640:360 output.mp4

shell> ffmpeg -i input.mp4 -i img.png -filter_complex overlay output.mp4  

shell> ffmpeg -i input.mp4 -i img.png -filter_complex overlay=W-w:H-h out.mp4
shell> ffmpeg -i input.mp4 -i img.png -ss 0 -t 10 -filter_complex overlay=x=W-w-10:y=H-h-10 out.mp4

shell> ffmpeg -i input.mp4 -i img.png -vcodec libx264 -filter_complex overlay -f flv rtmp://127.0.0.1:1935/mytv/live

shell> ffmpeg -i input.mp4 -i img.png -vcodec libx264 -filter_complex overlay=x=W-w-10:y=H-h-10 -f flv rtmp://127.0.0.1:1935/mytv/live

shell> ffmpeg -i input.mp4 -i img.png -vcodec libx264 -preset ultrafast -filter_complex overlay output.mp4 
```

`-framerate 6`
`-video_size vga`
`-video_size hd720`
`-video_size 1280x720`
`-video_size hd1080`
`-video_size 1920x1080`

`-preset ultrafast`
`-preset veryslow`

`Real-Time Messaging Protocol.`

`-b:a 64k`
`-b:a 128k`
`-b:v 800k`
`-b:v 1000k`

`-c copy`
`-c:a aac`
`-c:a mp2`
`-c:a libfdk_aac`
`-c:v copy`
`-c:v libx264`
`-c:v libx265`
`-c:v libvpx-vp9`

`-q:v 10`

`-i input.mp4`
`-i /dev/sr0`
`-i input.flv`
`-i input.wav`

`-f avfoundation`
`-f lavfi`
`-f libcdio`
`-f openal`
`-f flv`
`-f caca`
`-f fbdev`
`-f xv`
`-f oss`
`-f alsa`
`-f x11grab`
`-f image2`
`-f live_flv`
`-f v4l2`

`-pix_fmt rgb24`
`-pix_fmt uyvy422`
`-pix_fmt bgra`
`-pix_fmt yuv420p`

`-s 640x480`
`-s 720x486`
`-r 24000/1001`

`-window_size 80x25`
`-window_size qcif`

`-video_size cif`

`-framerate 25`
`-framerate 10`

`-re`

`-pattern_type glob`

`-codec copy`
`-codec:v libtheora`
`-codec:a libfdk_aac`
`-codec:a libmp3lame`

`-acodec libfaac`
`-acodec libmp3lame`
`-acodec ac3_fixed`
`-acodec copy`

`-vcodec rawvideo`
`-vcodec libx264`
`-vcodec copy`
`-c copy`

`-minrate 4000k`
`-maxrate 4000k`
`-bufsize 1835k`

`rtmp://myserver/vod/sample`
`rtmp://148.72.245.43:1935/mytv/live`
`rtmp://username:password@myserver/`

`/dev/null`

`ultrafast`
`superfast`
`veryfast`
`faster`
`fast`
`medium`
`slow`
`slower`
`veryslow`
`placebo`

`img.jpeg`
`img.png`
`test.avi`
`foo.mpg`
`foo.mov`
`foo.avi`
`a.mov`
`b.mov`
`stereo.wav`
`h264.mp4`
`sub.txt`
`file.mov`
`video.mkv`
`hugefile.yuv`

`video1.webm`
`video2.webm`
`audio1.webm`
`audio2.webm`

`input.gif`
`input.ts`
`input.wav`
`input.avi`
`input.mp4`
`input.mxf`
`input.flac`
`input.mkv`
`input.mpg`

`test1.avi`
`test2.avi`

`in.avi`
`in.mkv`
`in.ogg`

`myfile.avi`
`mydivx.avi`
`myfile.flv`

`output.mkv`
`output.m4a`
`output.mp4`
`output.flv`
`output.avi`
`output.mov`

`out.flv`
`out.gif`
`out.h264`
`out.mkv`
`out.mov`
`out.mpg`
`out.mpeg`
`out.ogg`
`out.ts`
`out.ttf`
`out.wav`
`out.mp3`
`out.m2v`
`out.sha256`
`out.m3u8`
`out.md5`
`out1.ogg`
`out2.ogg`


#### :books: 參考網站：
- [ffmpeg](https://ffmpeg.org/)
- [ffmpeg](https://ffmpeg.org/ffmpeg.html)
- https://ffmpeg.zeranoe.com/builds/
- https://www.ffmpeg.org/ffmpeg-devices.html
- https://www.ffmpeg.org/ffmpeg-all.html
- https://ffmpeg.org/ffmpeg-protocols.html
- https://ffmpeg.org/ffmpeg-utils.html
- https://ffmpeg.org/ffmpeg-filters.html#overlay-1
- http://manpages.ubuntu.com/manpages/xenial/man1/ffmpeg-codecs.1.html 


