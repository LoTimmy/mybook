### 安裝 {#installing}

```
shell> sudo apt-get update && sudo apt-get install build-essential openssl libreadline6 libreadline6-dev curl git-core zlib1g zlib1g-dev libssl-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev autoconf libc6-dev libncurses5-dev automake libtool bison subversion pkg-config
shell> \curl -sSL https://get.rvm.io | bash -s stable
shell> source /etc/profile.d/rvm.sh
shell> rvm list known
shell> rvm install 2.4
shell> rvm use 2.4
shell> ruby -v

shell> gem install bundler rails
shell> gem install thin
```

uglifier

```
shell> rails new web01
```

- `config/database.yml`
- `Gemfile`

```
shell> thin install
shell> sudo /usr/sbin/update-rc.d -f thin defaults
```

``` 
shell> thin config -C /etc/thin/web01 -c /root/web01 --servers 3 -e development
```

#### :books: 參考網站：
- https://www.ruby-lang.org/en/documentation/
- https://www.ruby-lang.org/en/documentation/installation/