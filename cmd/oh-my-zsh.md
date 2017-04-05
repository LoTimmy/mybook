```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

`.zshrc`

```
plugins=(git bundler osx rake ruby)
ZSH_THEME="robbyrussell"
ZSH_THEME="agnoster"

fpath=(/usr/local/share/zsh-completions $fpath)
source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```

```
git clone https://github.com/powerline/fonts.git

cd fonts
./install.sh

cd ..
rm -rf fonts
```

zsh-syntax-highlighting

  source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh




- https://www.iterm2.com/
- https://github.com/powerline/fonts
