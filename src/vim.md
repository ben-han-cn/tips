# Verbs
- d
- D # delete from current pos to end of line
- c
- C # change from current pos to end of line
- y
- Y # yank one line
- >
- <
- . # repeat last action

# Preposition (used with verbs)
- i # inside
- a # around

# Move
- h,j,k,l
- w,e,b
- W,E,B(ignore all non-whitespace character including '-',',' etc) 
- 0
- $ 
- ( # begin of sentence
- ) # end of sentence

# Search
- /regex  # search next instance
- n
- N
- t
- T
- f
- F

# Block view mode inserting
ctrl-v into block mode (the cursor place will be the insert place)
select the lines wants to insert
shift-i into insert mode, then insert what you want
use esc come back to normal mode 

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
