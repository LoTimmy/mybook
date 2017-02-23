`wget - retrieves files from the web`

### 安裝 {#installing}

```console
shell> brew install wget
```

```console
shell> wget --spider https://www.google.com/textinputassistant/tia.png
shell> wget -nv --spider https://www.google.com/textinputassistant/tia.png
```
```console
shell> wget --mirror --convert-links --adjust-extension --page-requisites --no-parent http://getbootstrap.com/
shell> wget -mkEpnp http://getbootstrap.com/      
```

```console
shell> wget -r --no-parent http://getbootstrap.com/
```

```console
shell> wget --content-disposition http://jpgraph.net/download/download.php?p=11
```

`~/.wgetrc`
```
# You can set the default proxies for Wget to use for http, https, and ftp.
# They will override the value in the environment.
#https_proxy = http://proxy.yoyodyne.com:18023/
#http_proxy = http://proxy.yoyodyne.com:18023/
#ftp_proxy = http://proxy.yoyodyne.com:18023/
     
# If you do not want to use proxy at all, set this to off.
#use_proxy = on
   
# Force the default system encoding
#locale = UTF-8
     
# Force the default remote server encoding
#remoteencoding = UTF-8

content_disposition = on
```
