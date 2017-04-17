![](https://handbrake.fr/docs/en/images/icon-1.0.0.png)

### 安裝 {#installing}

```console
shell> brew install handbrake
```

`HandBrakeCLI - versatile DVD ripper and video transcoder (command line)`


```console
shell> mkvpropedit movie.mkv --tags all:
shell> mkvpropedit input.mkv --edit track:s1 --set language=chi

shell> HandBrakeCLI
shell> HandBrakeCLI -i input.mkv -o output.mp4 --preset="High Profile" -s scan -F --subtitle-burned -N chi

shell> HandBrakeCLI -i input.mkv -o output.mp4 --preset="Very Fast 1080p30" -s scan -F --subtitle-burned -N chi
shell> HandBrakeCLI -i input.mkv -o output.mp4 --preset="Fast 1080p30" -s scan -F --subtitle-burned -N chi
shell> HandBrakeCLI -i input.avi -o output.mp4 --preset="iPhone & iPod touch"
```

```console
shell> HandBrakeCLI --help
shell> HandBrakeCLI --preset-list
```

#### :books: 參考網站：
- https://handbrake.fr/docs/en/latest/cli/cli-guide.html
- https://handbrake.fr/docs/en/latest/technical/official-presets.html
- http://manpages.ubuntu.com/manpages/zesty/man1/HandBrakeCLI.1.html


