
```console 
shell> mkvmerge --no-subtitles --title '' -o mymovie.mkv input.mkv
shell> mkvmerge -o mymovie.mkv input.mkv zh-TW.idx
shell> mkvmerge -o mymovie.mkv input.mkv zh-TW.srt  
```

```console 
shell> mkvmerge -o MM-complete.mkv MyMovie-with-sound.mkv MyMovie-add-audio.ogg
shell> mkvmerge -o MM-complete.mkv -A MyMovie.avi MyMovie.ogg MyMovie-add-audio.ogg
shell> mkvmerge -o output.mkv --language 0:fre franASais.ogg --language 0:deu deutsch.ogg
```

```console 
shell> mkvmerge --list-languages
```

```
English language name                                                            | ISO639-2 code | ISO639-1 code
---------------------------------------------------------------------------------+---------------+--------------
Chinese                                                                          | chi           | zh           
English                                                                          | eng           | en
Japanese                                                                         | jpn           | ja           
Korean                                                                           | kor           | ko           
```

```console 
shell> mkvpropedit movie.mkv --tags all:
```

```console 
shell> mkvpropedit movie.mkv --edit info --set "title=The movie" --edit track:a1 --set language=fre --edit track:a2 --set language=ita
shell> mkvpropedit movie.mkv --edit track:s1 --set flag-default=0 --edit track:s2 --set flag-default=1
shell> mkvpropedit movie.mkv --edit track:s1 --set language=fre
shell> mkvpropedit movie.mkv --edit track:s1 --set language=chi
shell> mkvpropedit movie.mkv --edit track:s3 --set name="中文(简体)"
shell> mkvpropedit movie.mkv --edit track:s2 --set name="中文(香港)"
shell> mkvpropedit movie.mkv --edit track:s1 --set name="中文(繁體)"

```

#### :books: 參考網站：
- [mkvmerge](https://mkvtoolnix.download/doc/mkvmerge.html)
- [mkvpropedit](https://mkvtoolnix.download/doc/mkvpropedit.html)

```
mkvmerge -o mymovie.mkv mymovie.avi mymovie.srt
HandBrakeCLI
mkvmerge
mkvinfo
mkvextract
mkvpropedit
input.mkv
file.mkv
movie.mkv

java -jar BDSup2Sub
java -jar BDSup2Sub.jar --help
java -jar BDSup2Sub.jar
```
