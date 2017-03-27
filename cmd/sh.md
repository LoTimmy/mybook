
```sh
#!/bin/sh
```

```sh
tar xzvf /path/to/<FILE>.tar.gz
unzip /path/to/<FILE>.zip
```

```sh
set -e
set +e

set -o xtrace
set -o pipefail
```

```sh
sleep 1
```

```sh
# Turn on checkwinsize
shopt -s checkwinsize
```

```sh
sed 's/\/.*//'
sed 's/\..*//'
sed 's/Server*//'
```

```sh
cut -d" " -f2,3 /proc/mounts
cut -d= -f2
cut -d' ' -f4
```

```sh
test -x $DAEMON || exit 0
```

```sh
if [ -x /usr/sbin/aa-status ]; then
  aa-status --verbose
else
  cat "$AA_SFS"/profiles
fi

if [ $ret -eq 0 ] && [ -x "$node" ]; then
else
fi
```

```sh
TMP="${TMPDIR}"
if [ "x$TMP" = "x" ]; then
  TMP="/tmp"
fi

tar="${TAR}"
if [ -z "$tar" ]; then
  tar="${npm_config_tar}"
fi
if [ -z "$tar" ]; then
  tar=`which tar 2>&1`
  ret=$?
fi
```



```sh
tr '[:upper:]' '[:lower:]'
tr -d '[[:space:]]'
```

```sh
export DEBIAN_FRONTEND=noninteractive
```

```sh
lsb_dist=debian
dist_version="$(cat /etc/debian_version | sed 's/\/.*//' | sed 's/\..*//')"
```




```sh
command_exists() {
  command -v "$@" > /dev/null 2>&1
}

if command_exists lsb_release; then
fi
```

```sh
curl=''
if command_exists curl; then
  curl='curl -sSL'
elif command_exists wget; then
  curl='wget -qO-'
elif command_exists busybox && busybox --list-modules | grep -q wget; then
  curl='busybox wget -qO-'
fi
```

```sh
cat <<-EOF

EOF
```

```sh
lsb_dist=''
dist_version=''
if command_exists lsb_release; then
  lsb_dist="$(lsb_release -si)"
fi
if [ -z "$lsb_dist" ] && [ -r /etc/lsb-release ]; then
  lsb_dist="$(. /etc/lsb-release && echo "$DISTRIB_ID")"
fi
if [ -z "$lsb_dist" ] && [ -r /etc/debian_version ]; then
  lsb_dist='debian'
fi
if [ -z "$lsb_dist" ] && [ -r /etc/fedora-release ]; then
  lsb_dist='fedora'
fi
if [ -z "$lsb_dist" ] && [ -r /etc/oracle-release ]; then
  lsb_dist='oracleserver'
fi
if [ -z "$lsb_dist" ] && [ -r /etc/centos-release ]; then
  lsb_dist='centos'
fi
if [ -z "$lsb_dist" ] && [ -r /etc/redhat-release ]; then
  lsb_dist='redhat'
fi
if [ -z "$lsb_dist" ] && [ -r /etc/os-release ]; then
  lsb_dist="$(. /etc/os-release && echo "$ID")"
fi

lsb_dist="$(echo "$lsb_dist" | tr '[:upper:]' '[:lower:]')"

# Special case redhatenterpriseserver
if [ "${lsb_dist}" = "redhatenterpriseserver" ]; then
  # Set it to redhat, it will be changed to centos below anyways
  lsb_dist='redhat'
fi
```

```sh
curl -f -L -s https://www.npmjs.org/install.sh > npm-install-$$.sh
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```


```sh
chown -R root:www /var/www
chmod 2775 /var/www
find /var/www -type d -exec chmod 2775 {} +
find /var/www -type f -exec chmod 0664 {} +
echo "<?php phpinfo(); ?>" > /var/www/html/phpinfo.php
```


#### :books: 參考網站：
- https://get.docker.com/
- https://experimental.docker.com/
- https://npmjs.com/install.sh