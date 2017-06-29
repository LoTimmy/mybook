<img src="http://brew.sh/img/homebrew-256x256.png" width="100">

`Homebrew` 

---

```console
shell> /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
shell> brew doctor
```

---

```console
shell> brew update
shell> brew upgrade --all

shell> brew list
shell> brew list --versions

shell> brew help

shell> brew search

shell> brew cleanup
shell> brew outdated

shell> brew info
```

---

```console
shell> brew install git

shell> brew install ssh-copy-id

shell> mkdir ~/.nvm
shell> cp $(brew --prefix nvm)/nvm-exec ~/.nvm/

shell> export NVM_DIR=~/.nvm
shell> source $(brew --prefix nvm)/nvm.sh

shell> nvm install v0.12.2
shell> nvm use 0.12.2
shell> nvm alias default 0.12.2

shell> brew install mongodb
shell> brew services start mongodb 
shell> brew services list

shell> killall Finder

shell> brew install most
shell> brew install whatmask
shell> brew install geoip
shell> brew install geoipupdate
shell> brew install archey
shell> brew install pwgen
shell> brew install p7zip

shell> brew install ec2-api-tools
shell> brew install ec2-ami-tools

shell> brew install gnu-tar --with-default-names
shell> brew install gnu-sed --with-default-names
shell> brew install findutils --with-default-names

shell> whatmask 192.168.5.6/22


shell> brew install rename

shell> brew install jmeter --with-plugins

shell> brew install the_silver_searcher
```

```console
shell> brew install caskroom/cask/brew-cask

shell> brew cask list

shell> brew cask search '/^google.c[a-z]rome$/'

shell> brew cask info mplayerx
shell> brew cask info unity-web-player
shell> brew cask info google-chrome

shell> brew cask install java
shell> brew cask install google-chrome
shell> brew cask install dropbox
shell> brew cask install airserver
shell> brew cask install vmware-fusion
shell> brew cask install mplayerx
shell> brew cask install unity-web-player
shell> brew cask install atom
shell> brew cask install visual-studio-code
shell> brew cask cleanup

shell> brew cask install skype
shell> brew cask install paragon-ntfs
shell> brew cask install paragon-extfs
shell> brew cask install paragon-vmdk-mounter

shell> brew cask install turbo-boost-switcher
shell> brew cask install synology-cloud-station-drive

shell> brew cask install adobe-photoshop-cc
shell> brew cask install adobe-illustrator-cc


shell> brew cask install virtualbox
shell> brew install docker
shell> brew install boot2docker

shell> brew cask install dropbox

shell> brew install bash-completion
shell> brew install lftp
shell> brew install wget
shell> brew install aria2
shell> brew install nvm
shell> brew install ssh-copy-id
shell> brew install coreutils
shell> brew install vim --with-override-system-vi

s3cmd
```

#### :books: 參考網站：
- https://github.com/caskroom/homebrew-cask/blob/master/USAGE.md

<!--
```
vmware-fusion
5G19L-13E7E-H4MWT-54DGP-5LQZ1
1VWJV-540AV-H4HNR-HW2QK-DYZ23
TAWWT-9HKW4-H4NM6-57UN3-66E6E
EYWDT-WHW7Y-H4WRR-8EMX0-0AGNE
ZFHN1-D2DGE-44HRH-7NC5H-1GG49
```
-->

```console
shell> brew install dlite
shell> brew upgrade dlite

shell> sudo dlite install
shell> sudo dlite install --help
shell> dlite stop
shell> dlite update

shell> dlite start
```

---

```console
shell> brew cask install ngrok
```

---

```console
shell> brew cask install virtualbox
shell> brew cask install virtualbox-extension-pack
```
---


```console
shell> brew cask install dropbox
```

---

**Add the following lines to your ~/.bash_profile:**

```
  if [ -f $(brew --prefix)/etc/bash_completion ]; then
    . $(brew --prefix)/etc/bash_completion
  fi
```

```console
shell> brew install caskroom/cask/brew-cask
shell> brew cask install google-chrome
shell> ls /opt/homebrew-cask/Caskroom
```

---

```console
shell> brew cask install handbrakecli

shell> brew install handbrakecli
```

```console
shell> HandBrakeCLI
shell> HandBrakeCLI -i -o  --preset="High Profile" -s scan -F --subtitle-burned -N chi
shell> HandBrakeCLI -i MyMovie.mkv -o MyMovie.avi --preset="High Profile" -s scan -F --subtitle-burned -N chi    
```

```console
shell> HandBrakeCLI --help
```

#### :books: 參考網站：
- https://handbrake.fr/docs/en/latest/cli/cli-guide.html

---

```console
shell> killall Finder

shell> brew install most
shell> brew install whatmask
shell> brew install geoip
shell> brew install geoipupdate
shell> brew install archey
shell> brew install pwgen
shell> brew install p7zip
shell> brew install ansible

shell> brew install redis

To have launchd start redis now and restart at login:
  brew services start redis
Or, if you don't want/need a background service you can just run:
  redis-server /usr/local/etc/redis.conf

shell> brew install rethinkdb

To have launchd start rethinkdb now and restart at login:
  brew services start rethinkdb
Or, if you don't want/need a background service you can just run:
  rethinkdb
```

```console
shell> brew install dnscrypt-proxy
```
---

```console
shell> brew cask install tuntap
```

---

#### :books: 參考網站：
- [brew](http://brew.sh/)
- [brew cask](http://caskroom.io/)
