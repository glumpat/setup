# Setting up Arch

## Installation

## Setup

#### Basics

```bash
sudo pacman -Sy --noconfirm base-devel git curl openssh inetutils
```

#### Github

```bash
ssh-keygen -b 4096 -t rsa -N '' -q -C "$USER" -f "$HOME/.ssh/id_rsa"
curl -o /dev/null \
    -s -w "%{http_code}\n" \
    -H "Authorization: token $TOKEN"
    --data "{\"title\":\"$USER@$(hostname)"\",\"key\":\"$(cat ~/.ssh/id_rsa.pub)\"}" \
    https://api.github.com/user/keys
ssh-keyscan github.com >> "$HOME/.ssh/known_hosts" 2>/dev/null
```

#### Setup Yay

```bash
git clone https://aur.archlinux.org/yay.git 
makepkg -si --noconfirm 
```

#### Desktop

```bash
yay -S --noconfirm \
    betterlockscreen \
    compton \ 
    dunst \ 
    feh \
    gnome \
    gnome-tweaks \
    i3-gaps \
    jsoncpp \
    polybar \
    rofi \
    xorg-xinit\
    xorg-xprop \ 
    lxappearance \
    nordic-theme-git 
```
 
#### CLI

```bash
yay -S --noconfirm \
    alacritty \
    diff-so-fancy \
    fzf \
    gvim \
    hub \
    jq \
    httpie \
    ripgrep \
    thefuck \
    tmux \
    zsh
```
 
#### Starship Prompts
 
```
 curl -fsSL https://starship.rs/install.sh | bash
```

#### Browsers & Dev Tookls

```bash
yay -S --noconfirm \
    chromium \
    docker \
    docker-compose \
    firefox-developer-edition \
    jetbrains-toolbox 
```

#### Utilities & Drivers

```bash
yay -S --noconfirm \
    arandr \
    ctags \
    dialog \
    easyeffects \
    htop \
    mesa \
    neofetch \
    network-manager-applet \
    networkmanager \
    pavucontrol \
    pipewire \
    pipewire-pulse \
    pipewire-gst-plugin-pipewire \
    ranger \
    redshift \
    reflector \
    screenkey \
    w3m \
    wget \
    xclip \
    xournal \
    xorg-xrandr 
```

```bash
sudo systemctl enable NetworkManager.service
```

#### Random Apps

```bash
yay -S --noconfirm \
    gimp \
    inkscape \
    speedcrunch \
    spotify \
    syncthing \
    syncthingtray \
    slack \
    vlc \
    zathura \
    zathura-pdf-mupdf 
```

#### Homeshick

```bash
homeshick_root="$HOME/.homesick/repos/homeshick"
homeshick_bin="$homeshick_root/bin/homeshick"

git clone git@github.com:andsens/homeshick.git "$homeshick_root" 

"${homeshick_bin}" clone --batch git@github.com:glumpat/dotfiles.git
"${homeshick_bin}" link --force
```

#### ZSH

```bash
sudo chsh -s "/bin/zsh" "$USER" 
```

#### Zinit

```bash
mkdir $HOME/.zinit
git clone https://github.com/zdharma/zinit.git $HOME/.zinit/bin
```

#### TPM

```bash
local tpm_root="$HOME/.tmux/plugins/tpm"
git clone git@github.com:tmux-plugins/tpm.git  "$tpm_root"
"$tpm_root/scripts/install_plugins.sh"
```

#### ASDF

```bash
asdf_root="$HOME/.asdf"

git clone  git@github.com:asdf-vm/asdf.git "$asdf_root"
```

#### asdf-ruby / asdf-node / asdf-python

```bash
# Ruby
asdf plugin-add ruby
asdf install ruby $(asdf latest ruby)
# Python
asdf plugin-add python
asdf install python $(asdf latest python)
# Node
asdf plugin-add nodejs
"$HOME/.asdf/plugins/nodejs/bin/import-release-team-keyring"
asdf install nodejs $(asdf latest nodejs)
```

#### GDM

```bash
sudo systemctl enable gdm
```

#### Docker

```bash
sudo usermod -aG docker "$USER" 
sudo systemctl enable docker
```


#### Fonts

```bash
yay -S --noconfirm \
    ttf-font-awesome \
    ttf-material-icons-git 
```

#### Nerd Fonts

```bash
mkdir ~/Downloads && cd ~/Downloads
yay --getpkgbuild nerd-fonts-complete && cd nerd-fonts-complete
wget -O nerd-fonts-2.1.0.tar.gz https://github.com/ryanoasis/nerd-fonts/archive/v2.1.0.tar.gz
makepkg -sci BUILDDIR=.
```

#### Better Lockscreen

```
mkdir -p ~/Pictures/Backgrounds
wget -O ~/Pictures/Backgrounds/forest.jpg https://i.imgur.com/lhZoAOv.jpg
wget -O ~/Pictures/Backgrounds/mountains.jpg https://i.imgur.com/zuNUJ4J.jpg
wget -O ~/Pictures/Backgrounds/moss.jpg https://i.imgur.com/kTNHsRt.jpg
wget -O ~/Pictures/Backgrounds/cliff.jpg https://i.imgur.com/hdXF561.jpg
wget -O ~/Pictures/Backgrounds/mountainlake.jpg https://i.imgur.com/ymmraHp.jpg
wget -O ~/Pictures/Backgrounds/autumn.jpg https://i.imgur.com/f5YDfNq.jpg
wget -O ~/Pictures/Backgrounds/tundra.jpg https://i.imgur.com/g9h0kkl.jpg
betterlockscreen -u ~/Pictures/Backgrounds
```