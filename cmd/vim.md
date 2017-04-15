<img src="http://i.imgur.com/VzpZv22.png" width="100">

---
<kbd>Ctrl</kbd> + <kbd>V</kbd>, <kbd>Ctrl</kbd> + <kbd>M</kbd>

```
:%s/^M//g
```
---

`xterm-256color`

```console
shell> echo $TERM   
```

`.vimrc`
```vim
set t_Co=256
```

```
:runtime syntax/colortest.vim
```
```
:set t_Co?
```

---

`.vimrc`
```vim
" Don't use vi-compatibility mode
set nocompatible
```

```vim
" Use UTF-8 as the default text encoding
set encoding=utf-8
```

```vim
" Delete Line
map <silent> <C-E> dd
" Duplicate Line
map <silent> <C-D> yyp
```

```vim
syntax on
colorscheme desert
```

```
:colorscheme 
```

---

```vim
set modeline
```

```
// vim: number ruler
```

---

`.vimrc`

```vim
" Maintainer: Timmy Lo <timmylo@kimo.com>
" Last change:  2015 Apr 15

set ignorecase
set ruler          " show the cursor position all the time

set expandtab
set tabstop=2
set softtabstop=2

autocmd BufNewFile  *.c 0r ~/vim/skeleton.c
autocmd BufNewFile  *.java  0r ~/vim/skeleton.java
autocmd BufNewFile  *.html  0r ~/vim/skeleton.html

" Key mappings
nnoremap <F2> :set number!<CR>
nnoremap <F5> :set list!<CR>
nnoremap <F9> :Explore<CR>

function! ToggleSyntax()
   if exists("g:syntax_on")
      syntax off
   else
      syntax enable
   endif
endfunction

" Toggle syntax setting on/off
map <F4> :execute ToggleSyntax()<CR>

" Delete Line
map <silent> <C-E> dd
" Duplicate Line
map <silent> <C-D> yyp

" set number
" set background=dark
" set cursorline

set statusline=%F%m%r%h%w\ [FORMAT=%{&ff}]\ [TYPE=%Y]\ [ASCII=\%03.3b]\ [HEX=\%02.2B]\ [POS=%04l,%04v]\ [%p%%]\ [LEN=%L]
set laststatus=2

if has("autocmd")
  au BufReadPost * if line("'\"") > 1 && line("'\"") <= line("$") | exe "normal! g'\"" | endif
endif
```

---

```vim
if has("autocmd")
  autocmd BufReadPost *
    \ if line("'\"") > 0 && line("'\"") <= line("$") |
    \   exe "normal g`\"" |
    \ endif
endif " has("autocmd")
```

#### :books: 參考網站：
- https://en.opensuse.org/SDB:VIM_disable_line_resume
- [autocmd](http://vimdoc.sourceforge.net/htmldoc/autocmd.html)

---

```
set nocompatible
set encoding=utf-8
set softtabstop=4
set tabstop=4
set shiftwidth=4
set undolevels=1024
set history=64
set modelines=32
set modeline
set backup
set ruler
set showmatch
set hlsearch
set incsearch
set ignorecase
set smartcase
set autoindent
set backspace=indent,eol,start
set wildmenu
set showcmd
set nobackup
set nofoldenable

filetype indent plugin on
syntax on

map <PageUp> <C-u>
map <PageDown> <C-d>
imap <PageUp> <C-o><C-u>
imap <PageDown> <C-o><C-d>

inoremap <Esc>Oq 1
inoremap <Esc>Or 2
inoremap <Esc>Os 3
inoremap <Esc>Ot 4
inoremap <Esc>Ou 5
inoremap <Esc>Ov 6
inoremap <Esc>Ow 7
inoremap <Esc>Ox 8
inoremap <Esc>Oy 9
inoremap <Esc>Op 0
inoremap <Esc>On .
inoremap <Esc>OQ /
inoremap <Esc>OR *
inoremap <Esc>Ol +
inoremap <Esc>OS -
inoremap <Esc>OM <Enter>

```

---

`/usr/share/vim/vim73/colors`

`/usr/share/vim/vim73/filetype.vim`

```
:edit $VIMRUNTIME/colors/README.txt
```


```console
shell> vimdiff file1 file2
```

---

```console
shell> git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```

`.vimrc`
```
set nocompatible
filetype off

set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()

Plugin 'VundleVim/Vundle.vim'
Plugin 'maksimr/vim-jsbeautify'

call vundle#end()
filetype plugin indent on

map <c-f> :call JsBeautify()<cr>

```

`.editorconfig`
```
;.editorconfig

root = true

[**.js]
; path to optional external js beautifier, default is vim-jsbeautify/plugin/lib
path=~/.vim/bundle/js-beautify/js/lib/beautify.js
; Javascript interpreter to be invoked by default 'node'
bin=node
indent_style = space
indent_size = 2

[**.css]
path=~/.vim/bundle/js-beautify/js/lib/beautify-css.js
indent_style = space
indent_size = 2

[**.html]
; Using special comments
; And such comments or apply only in global configuration
; So it's best to avoid them
;vim:path=~/.vim/bundle/js-beautify/js/lib/beautify-html.js
;vim:max_char=78:brace_style=expand
indent_style = space
indent_size = 2
```


```
:PluginInstall
```

```console
shell> vim +PluginInstall +qall
shell> cd ~/.vim/bundle/vim-jsbeautify && git submodule update --init --recursive
```

#### :books: 參考網站：
- [Vundle](https://github.com/VundleVim/Vundle.vim)
- [vim-jsbeautify](https://github.com/maksimr/vim-jsbeautify)


---

```
filetype plugin indent on

set foldmarker={{{,}}}
set foldmethod=marker
set foldlevel=0
```

`zo`
`zc`
`zr`
`zm`

---

#### :books: 參考網站：
- http://vimdoc.sourceforge.net/htmldoc/options.html
- http://public.dhe.ibm.com/software/dw/aix/sample.vimrc
