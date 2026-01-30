# My Dotfiles 
also  don't forget  to  comment this if u don't wan't this feature
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

# Close App
```bash
super + {_,shift + }c
	bspc node -{c,k}
```
to this : 
```bash
super + {_,shift + }q
	bspc node -{c,k}
```
##### step ??? :  
just  add these lignes under the .config/bspwm/sxhkdrc file : 

remove or comment these lignes to provent navigation errors : 
```bash
# Switch workspace
ctrl + alt + {Left,Right}
    bspc desktop -f {prev.local,next.local}

# Switch workspace or Send focused Node to another workspace
super + {_,shift + }{1-8}
	bspc {desktop -f,node -d} '^{1-8}' '--follow
```
then , just  add these lignes under the .config/bspwm/sxhkdrc file : 
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

##### step ???++ : 
###### preview : 
<img width="945" height="510" alt="image" src="https://github.com/user-attachments/assets/7da48145-44d9-48a8-ac21-4b77b3d651f8" />

- the goal  here is to  make animated neofetch using piewdipie config files just  remember to  add this files to my .zshrc file :
  I'made it shows only if I'm on alacrity  since it don't work fine with 
```bash
if [[ "$term" == "alacritty" ]]; then
if [[ -n $ps1 ]]; then
   ~/.config/neofetch/animated-neofetch.sh 0.05
  clear
fi
fi
```
---

###### step ??? +2 :
add designer to app luncher app : 
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
