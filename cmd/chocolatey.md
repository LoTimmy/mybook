
```console
shell> @powershell -NoProfile -ExecutionPolicy unrestricted -Command "(iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))) >$null 2>&1" && SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin
```

```console
shell> iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))
```

```console
shell> choco
Chocolatey v0.9.9.11 
```

```console
shell> choco install mkvtoolnix
shell> choco install ffmpeg

shell> choco install googlechrome
shell> choco install firefox
shell> choco install jre8
shell> choco install adobereader
shell> choco install git.install
shell> choco install ccleaner
shell> choco install dropbox
shell> choco install python
shell> choco install python2
shell> choco install pip
shell> choco install ruby
shell> choco install youtube-dl
shell> choco install cygwin
shell> choco install dotnet4.0
shell> choco install rdcman

shell> choco install skype
shell> choco install filezilla
shell> choco install 7zip
shell> choco install nodejs
shell> choco install putty
shell> choco install virtualbox
shell> choco install php
shell> choco install virtualclonedrive


shell> choco install winscp.install
shell> choco install mariadb

```


### :books: 參考網站：

- [chocolatey](https://chocolatey.org/)
- [packages](https://chocolatey.org/packages)
