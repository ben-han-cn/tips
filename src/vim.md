# Verbs
- x "delete the character
- r "replace the character
- s "delete the character and move to insert mode
- d
- D "delete from current pos to end of line
- c
- C "change from current pos to end of line
- y
- Y "yank one line
- > "ident
- <
- . "repeat last action
- g; "jump to last change you made
- g, "jump back forward through the change list
# Nouns 
## Preposition
- i "inside
  - iw, it, i", ip
- a "around
  - ap

## Move 
- h,j,k,l
- w,e,b
- W,E,B(ignore all non-whitespace character including '-',',' etc) 
- 0
- $ 
- ( " begin of sentence
- ) " end of sentence
- H(high),M(middle),L(low)
- v " before move will flip the inclusive/exclusive of the move

## move Command
5,7m0 "move line from 5 to 7 to the beginning of the file.   
m+1   "move current line down one line

## Search/Parameterized Text objects
- /regex  "search next instance, d/foo d?bar
- t, T
- f, F
- n, N

# Line number
- Absolute line number, set nu!
- Relateive line number, set rnu!
- Hybrid line number, set nu! rnu!

# Block view mode inserting
ctrl-v into block mode (the cursor place will be the insert place)
select the lines wants to insert
shift-i into insert mode, then insert what you want
press esc twice which will apply changes to all lines

# copy selection to clipboard
//select all the text want to copy
w !pbcopy

# find file 
in vimrc
```text
set path+=**
set wildmenu
```

then in vim window
`find clien` follow by tab, will search any file begin with clien

# vim rust tag
- install racer
```shell
rustup toolchain add nightly
cargo +nightly install racer
rustup component add rust-src
```
- git clone --depth=1 https://github.com/racer-rust/vim-racer.git ~/.vim/bundle/vim-racer
- configure vim
```text
set hidden
let g:racer_cmd = "~/.cargo/bin/racer"
let g:racer_insert_paren = 1
augroup Racer
    autocmd!
    autocmd FileType rust nmap <buffer> gd         <Plug>(rust-def)
    autocmd FileType rust nmap <buffer> gs         <Plug>(rust-def-split)
    autocmd FileType rust nmap <buffer> gx         <Plug>(rust-def-vertical)
    autocmd FileType rust nmap <buffer> gt         <Plug>(rust-def-tab)
    autocmd FileType rust nmap <buffer> <leader>gd <Plug>(rust-doc)
augroup END
```

# File browsing
```text
let g:netrw_banner=0
let g:netrw_liststyle=3
```
:edit . //navigate the folder, use enter to into the sub folder
use o/v to open the file in different window

# rust dev env
- rust.vim
```shell
vim ~/.vimrc

syntax enable
filetype plugin indent on
git clone https://github.com/rust-lang/rust.vim ~/.vim/pack/plugins/start/rust.vim
```
- rust-analyzer
```shell
rustup component add rust-analyzer
```
- nvm — node
```shell
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
nvm install node
```
- vim-plug
```shell
curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

vim ~/.vimrc

call plug#begin()
call plug#end()
```
- coc.nvim
```shell
vim ~/.vimrc

call plug#begin()
Plug 'neoclide/coc.nvim', {'branch': 'release'}
call plug#end()

vim

:PlugInstall
```

- coc-rust-analyzer
```shell
vim

:CocInstall coc-rust-analyzer
```
- disable type hint
```shell
:CocConfig
"rust-analyzer.inlayHints.chainingHints": false,
"rust-analyzer.inlayHints.typeHints": fale,
"rust-analyzer.inlayHints.parameterHints": false
```
