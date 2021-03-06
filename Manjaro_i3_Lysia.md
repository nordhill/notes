
### cat /etc/lsb-release
```
DISTRIB_ID=ManjaroLinux
DISTRIB_RELEASE=20.0.3
DISTRIB_CODENAME=Lysia
DISTRIB_DESCRIPTION="Manjaro Linux"
``` 

### dotfiles location: /etc/skel/ skel="skeleton"
`mkdir ~/.config/i3 && cp /etc/skel/.i3/config ~/.config/i3/config`

`mkdir ~/.config/nvim && touch ~/.config/nvim/init.vim`

### apps to install
`sudo pacman -S neovim tmux firefox ripgrep`


### aliases
`touch ~/.bashrc_aliases`

Add to .bashrc: `source  ~/.bashrc_aliases`

```
alias g="git"
```

### neovim plugins
```
call plug#begin('~/.config/nvim/plugged')
Plug 'neoclide/coc.nvim', {'branch': 'release'}
Plug 'vim-airline/vim-airline'
Plug 'vim-airline/vim-airline-themes'
Plug 'junegunn/fzf', { 'do': { -> fzf#install() } }
Plug 'junegunn/fzf.vim'
Plug 'dense-analysis/ale'
call plug#end()
 
```
  
### neovim init.vim
```
" Use clipboard for yanking, copy and pasting
set clipboard=unnamedplus
" Allow recursive search from where neovim was opened from
set path=.,/usr/include,,**
" Don't wrap round to the first solution found when searching and navigating the results
:set nowrapscan
" Move to first search result when typing
:set incsearch
" Reload opened files if external commands cause changes
set autoread
" Use spaces instead of actual tabs when pressing tab
set expandtab
"
set smartcase
" allow using mouse in vim
set mouse a
"
filetype plugin indent on
" On pressing tab, insert 2 spaces
set expandtab
" show existing tab with 2 spaces width
set tabstop=2
set softtabstop=2
" when indenting with '>', use 2 spaces width
set shiftwidth=2
"Ignore in searchers
set wildignore+=**/node_modules/**
"Copy active file name to clipboard                                                                                                                             
noremap <silent <F4> :let @+=expand("%:p")<CR>
"Go to next and previous error with F8 and F9
nmap <silent> <F8> :ALENext<cr>
nmap <silent> <F9> :ALEPrevious<cr>
" Relative numbers
set nu rnu
" Open GFiles with Ctrl+p
noremap <C-p> :GFiles<CR>
```

#### Experimentals
``` 
 Plug 'yuezk/vim-js'                                                                                                                                                              
 Plug 'maxmellon/vim-jsx-pretty'                                                                                                                                                  
 Plug 'airblade/vim-gitgutter'                                                                                                                                                    
 Plug 'haya14busa/incsearch.vim'
 
vnoremap // y/\V<C-R>=escape(@",'/\')<CR><CR>

" Copy active file name to clipboard                                                                                                                                                 
noremap <silent> <F4> :let @+=expand("%:p")<CR>

set wildignore+=**/node_modules/**   

set incsearch
map /  <Plug>(incsearch-forward)                                                                                                                                                     
map ?  <Plug>(incsearch-backward)                                                                                                                                                    
map g/ <Plug>(incsearch-stay) 

command! -nargs=1 SS let @/ = '\V'.escape(<q-args>, '\')|set hlsearch      

nnoremap <C-c><C-c> :noh<return> 

syntax on

```


### coc-settings.json (~/.config/nvim/coc-settings.json)
```
{
 "suggest.noselect": false
}
```


### scripts
Watch for git log changes (no color)
```
watch -n 1  "sh -c 'git log | head -n $(tput lines)'"
watch --color git status
``` 
Keep colors even with watch script
```
git config color.status always
```

### resource links
* Essential keybinds for vim/neovim https://www.youtube.com/watch?v=gZCXaF-Lmco

### bash
Don't record duplicates to bash history for better history grepping
```
export HISTCONTROL=ignoreboth:erasedups
``` 

### open tmux in git project to start working (combine with tmux script to open splits)
```
COLUMNS=12

array=($(ls -d ~/git/*/ | cat))

select name in "${array[@]}"; do
    echo "Going to $name"
    cd $name
    tmux
    break
done
```

### other

* With Plug 'kristijanhusak/vim-js-file-import', {'do': 'npm install'} you had to install pynvim via "pip3 install pynvim"
* ctags was required with vim-js-file-import - this generates tags file that needs to be ignored in git. ctags is not supposed to go to node_modules etc so you need to create ~/.ctags file where you declare ignores e.g --exclude=node_modules

* To have color syntax in fuzzy finder, you need to have bat installed 

