`aria2 - High speed download utility`

### 安裝 {#installing}

```sh
shell> apt-get install aria2
shell> brew install aria2
shell> apt install aria2
```

**Download a file**

```sh
shell> aria2c http://example.org/mylinux.iso
```

**Download a file from 2 different HTTP servers**
```sh
shell> aria2c http://a/f.iso ftp://b/f.iso
shell> aria2c -o myfile.zip "http://mirror1/file.zip" "http://mirror2/file.zip"
```

```sh
shell> aria2c -x2 http://a/f.iso
shell> aria2c http://example.org/mylinux.torrent
shell> aria2c http://example.org/mylinux.metalink
```

`$HOME/.aria2/aria2.conf`
```
http-accept-gzip=true

ftp-pasv=true
ftp-reuse-connection=true

allow-overwrite=false
always-resume=true
auto-file-renaming=false
continue=true
remote-time=true

enable-dht=true
enable-peer-exchange=true
dht-listen-port=60000
listen-port=60000

disk-cache=0
file-allocation=none

summary-interval=0

seed-ratio=1.0
seed-time=120

disable-ipv6=true

follow-torrent=mem

bt-exclude-tracker="*"

max-upload-limit=50K
all-proxy=http://user:pass@proxy:8888
```

```sh
shell> screen -d -m aria2c http://example.org/mylinux.torrent
```

#### :books: 參考網站：
- [screen](https://www.gnu.org/software/screen/)
