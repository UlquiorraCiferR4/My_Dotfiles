

# My Dotfiles and sys configurations 

(っ◔◡◔)っ ♥ Hello There ♥

after  a fresh install of **archcraft** this is the steps I' pass throw to  get  my system  work the way  I'like So Let's start  :

---
####  - step 1  :
first thing to do  is to make timeshift snapshot to get the system working back  in state of falling : 

---
#### - step 2 : installing nvim 
So first we download nvim as text-editor :
```bash
sudo pacman -S nvim
```

I'use nvchad so I'do this right after : 

```bash
git clone https://github.com/NvChad/starter ~/.config/nvim && nvim
```

if u faced some problemes just like me you may  consider updating the system 

---
#### - step 3 : 
one of the things I'hate is how bspwm from archcraft open each app in  a spesific app
 ( you  may like it but I'personally don't like it )  So I'comment these lignes  in **.config/bspwm/bspwmrc** file (around ligne 100 ): 

```bash
## 1 > terminal (always open terminal on workspace-1)
bspc rule -a Alacritty desktop='^1' follow=on focus=on
bspc rule -a Xfce4-terminal desktop='^1' follow=on focus=on

## 2 > web (always open web browser on workspace-2)
bspc rule -a firefox desktop='^2' follow=on focus=on
bspc rule -a chromium desktop='^2' follow=on focus=on

## 3 > files (always open file manager on workspace-3)
declare -a files=(Pcmanfm Thunar qBittorrent)
for i in ${files[@]}; do
   bspc rule -a $i desktop='^3' follow=on focus=on; done

## 4 > code (always open editors on workspace-4)
declare -a code=(Geany code-oss)
for i in ${code[@]}; do
   bspc rule -a $i desktop='^4' follow=on focus=on; done

## 5 > office and docs (always open office/doc apps on workspace-5)
declare -a office=(Gucharmap Atril Evince \
libreoffice-writer libreoffice-calc libreoffice-impress \
libreoffice-startcenter libreoffice Soffice *:libreofficedev *:soffice)
for i in ${office[@]}; do
   bspc rule -a $i desktop='^5' follow=on focus=on; done

## 6 > communication (always open communication apps on workspace-6)
declare -a comm=(Thunderbird TelegramDesktop Hexchat)
for i in ${comm[@]}; do
   bspc rule -a $i desktop='^6' follow=on focus=on; done

## 7 > media (always open media apps on workspace-7)
declare -a media=(Audacity Music MPlayer Lxmusic Inkscape Gimp-2.10 obs)
for i in ${media[@]}; do
   bspc rule -a $i desktop='^7' state=floating follow=on focus=on; done

## 8 > system (always open system apps on workspace-8)
bspc rule -a 'VirtualBox Manager' desktop='^8' follow=on focus=on
bspc rule -a GParted desktop='^8' follow=on focus=on
declare -a settings=(Lxappearance Lxtask Lxrandr Arandr \
System-config-printer.py Pavucontrol Exo-helper-1 \
Xfce4-power-manager-settings)
for i in ${settings[@]}; do
   bspc rule -a $i desktop='^8' state=floating follow=on focus=on; done
```

#### -  Step 3 :  Close Apps
I'prefer closing apps using **super + Q** instead of **super + C** So I'change this : 
```bash
super + {_,shift + }c
	bspc node -{c,k}
```
to this : 
```bash
super + {_,shift + }q
	bspc node -{c,k}
```
##### step 4 :  ( navigation )
I'have 65% azerty keybord so I'change this : ( in .config/bspwm/sxhkdrc file )

```bash
# Switch workspace
ctrl + alt + {Left,Right}
    bspc desktop -f {prev.local,next.local}

# Switch workspace or Send focused Node to another workspace
super + {_,shift + }{1-8}
	bspc {desktop -f,node -d} '^{1-8}' '--follow
```
to this :
```bash
# ─────────────────────────────────
# navigate between workspaces 1–8 #
# ─────────────────────────────────
super + ampersand
    bspc desktop -f ^1
super + eacute
    bspc desktop -f ^2
super + quotedbl
    bspc desktop -f ^3
super + apostrophe
    bspc desktop -f ^4
super + parenleft
    bspc desktop -f ^5
super + minus
    bspc desktop -f ^6
super + egrave
    bspc desktop -f ^7
super + underscore
    bspc desktop -f ^8
# ──────────────────────────────────────
# Move focused window to  a workspace  #
# ──────────────────────────────────────
super + shift + ampersand
    bspc node -d ^1 --follow
super + shift + eacute
    bspc node -d ^2 --follow
super + shift + quotedbl
    bspc node -d ^3 --follow
super + shift + apostrophe
    bspc node -d ^4 --follow
super + shift + parenleft
    bspc node -d ^5 --follow
super + shift + minus
    bspc node -d ^6 --follow
super + shift + egrave
    bspc node -d ^7 --follow
super + shift + underscore
    bspc node -d ^8 --follow
```

---
##### step 5 : (using neofetch from piewdipie )
###### preview : 
<img width="945" height="510" alt="image" src="https://github.com/user-attachments/assets/7da48145-44d9-48a8-ac21-4b77b3d651f8" />

- the goal  here is to  make animated neofetch using piewdipie config just  follow this steps : 
```bash
git clone https://github.com/pewdiepie-archdaemon/dionysus.git
```
then remove the archcraft neofetch config  : 
```bash 
sudo rm -rf .config/neofetch
```
then move the downloaded files :
```bash
cp  -r dionysus-dionysus/dotfiles/neofetch 
```
last thing add these lines to  the bottom of the  .zshrc file : 
```bash
alias neofetch='./.config/neofetch/animated-neofetch.sh' 

if [[ -n $PS1 ]]; then
  ~/.config/neofetch/animated-neofetch.sh 0.05
  clear
fi
```

---
###### step 6 : install qt designer 

```bash
sudo pacman -S qt5-tools
```
add designer to app luncher app (rofi): 
```bash
mkdir -p ~/.local/share/applications
touch qt-designer.desktop
```

and after that paste these lignes in  qt-designer.desktop :

```bash
[Desktop Entry]
Name=Qt Designer
Comment=Design GUIs for Qt applications
# Change this path if 'which designer' gave you a different one
Exec=/usr/bin/designer
#Icon=designer
Icon =/usr/share/icons/Papirus-Apps/48x48/apps/designer-qt5.svg
Terminal=false
Type=Application
Categories=Development;GUIDesigner;Qt;
```
#### - step 7 make picom work properly 

I'make picom show a transparent terminal and firefix by :
```bash
blur: {
  method = "dual_kawase";
  strength = 6;
  background = true;
  background-frame = false;
  background-fixed = false;
}
rules = (
  {
    match = " class_g = 'firefox'||class_g = 'Alacritty' || class_g = 'obsidian' ";
    opacity = 0.9;          
    blur-background = true;
  }
)
```

#### - step 8 install  python env : 
first go  to the dir where you wan't to make the venv and write this down  : 

```bash
python3 -m venv .venv
```
 
 then  add this line to be able to  activate the env easly from any where  :
   
```bash
alias activate='source ~/Templates/coding/.venv/bin/activate'
```

--- 
#### - step 9 : install dir jumper (zoxide)

first  install zoxide : 

```bash 
sudo pacman -S zoxide
```

then  add these lines to  the bottm of your .zshrc file : 

```zsh
eval "$(zoxide init zsh)"
```

it won't work  directly but after some navigation it will  start helping you to  navigate better  between  apps 
