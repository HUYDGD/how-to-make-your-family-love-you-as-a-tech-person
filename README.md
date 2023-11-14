# huydgd-xubuntu-config
HUYDGD Xubuntu Config.

# Installation
## Themes
Themes: ```git clone https://github.com/vinceliuice/WhiteSur-gtk-theme.git --depth=1```
</br>
Icons: ```git clone https://github.com/vinceliuice/WhiteSur-icon-theme```
</br>
Wallpapers: ```git clone https://github.com/vinceliuice/WhiteSur-wallpapers```
<br>
Use install.sh to install all.
Choose theme & icons in Appearance menu. Don't forget to choose it in Window Manager too.

## ibus-bamboo
```sh
sudo add-apt-repository ppa:bamboo-engine/ibus-bamboo
sudo apt-get update
sudo apt-get install ibus ibus-bamboo --install-recommends
ibus restart
# Set ibus-bamboo as default keyboard
env DCONF_PROFILE=ibus dconf write /desktop/ibus/general/preload-engines "['BambooUs', 'Bamboo']" && gsettings set org.gnome.desktop.input-sources sources "[('xkb', 'us'), ('ibus', 'Bamboo')]"
```
<br>
Add this into $HOME/.bashrc

```sh
export GTK_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT_IM_MODULE=ibus
pidof ibus-daemon > /dev/null || ibus-daemon -drx
```

## Plank
```sh
sudo apt update
sudo apt install plank
plank
```
On login run: ```Session And Startup```
