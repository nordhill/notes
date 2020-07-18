
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
`sudo pacman -S neovim tmux firefox`


### aliases
`touch ~/.bashrc_aliases`

Add to .bashrc: `source  ~/.bashrc_aliases`

```
alias g="git"
```

### neovim init.vim
```
" Allow recursive search from where neovim was opened from
set path=.,/usr/include,,**
" Don't wrap round to the first solution found when searching and navigating the results
:set nowrapscan
" Move to first search result when typing
:set incsearch
" Reload opened files if external commands cause changes
set autoread
```

### scripts
Watch for git log changes (no color)
```
watch -n 1  "sh -c 'git log | head -n $(tput lines)'"
``` 
