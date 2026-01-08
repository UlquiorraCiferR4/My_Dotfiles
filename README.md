# My Dotfiles 




##### step ??? :  
just  add these lignes under the .config/bspwm/sxhkdrc file : 

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
```bash
if [[ -n $PS1 ]]; then
   ~/.config/neofetch/animated-neofetch.sh 0.05
  clear
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
