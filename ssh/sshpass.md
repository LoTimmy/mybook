`sshpass - Non-interactive ssh password authentication`


### 安裝 {#installing}

```console
shell> apt-get install sshpass
```

`sshpass.rb`
```rb
class Sshpass < Formula
  homepage "https://sourceforge.net/projects/sshpass/"
  url "http://nchc.dl.sourceforge.net/project/sshpass/sshpass/1.06/sshpass-1.06.tar.gz"
  sha256 "c6324fcee608b99a58f9870157dfa754837f8c48be3df0f5e2f3accf145dee60"

  def install
    system "./configure", "--prefix=#{prefix}"
    system "make", "install"
  end
end
```

```console
shell> brew install sshpass.rb
```

```console
shell> sshpass -p 12345 ssh -l username remotehost
shell> sshpass -p 12345 sftp username@remotehost
```

```console
shell> set +o history
shell> sshpass -p 12345 ssh -l username remotehost
shell> set -o history
```
