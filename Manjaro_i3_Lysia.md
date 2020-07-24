
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
