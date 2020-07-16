
### cat /etc/lsb-release
DISTRIB_ID=ManjaroLinux
DISTRIB_RELEASE=20.0.3
DISTRIB_CODENAME=Lysia
DISTRIB_DESCRIPTION="Manjaro Linux"

### dotfiles location: /etc/skel/ skel="skeleton"
`mkdir ~/.config/i3 && cp /etc/skel/.i3/config ~/.config/i3/config`
`mkdir ~/.config/nvim && touch ~/.config/nvim/init.vim`

### apps to install
`sudo pacman -S neovim`


### aliases
`touch ~/.bashrc_aliases`
Add to .bashrc: `source  ~/.bashrc_aliases`

`alias g="git"`
