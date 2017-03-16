
```sh
set -e
set +e
```
```
export DEBIAN_FRONTEND=noninteractive
```

```
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


#### :books: 參考網站：
- https://get.docker.com/
- https://experimental.docker.com/
- https://npmjs.com/install.sh