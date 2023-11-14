# huydgd-xubuntu-config
HUYDGD Xubuntu Config. Goal is a fastest desktop use for family watching TV and e-learning.

# Installation
## Themes
### My family love beautiful GUI.
Themes: ```git clone https://github.com/vinceliuice/WhiteSur-gtk-theme.git --depth=1```
</br>
Icons: ```git clone https://github.com/vinceliuice/WhiteSur-icon-theme```
</br>
Wallpapers: ```git clone https://github.com/vinceliuice/WhiteSur-wallpapers```
<br>
Use install.sh to install all.
Choose theme & icons in Appearance menu. Don't forget to choose it in Window Manager too.

## Set Default Audio Output Device
```sh
pactl list short sinks
pactl set-default-sink 'Your_Device_Name'
```

## Disable gnome-keyring
Parents shouldn't waste time with technology, all they need is fast and quality.
<br>
```sudo apt-get remove gnome-keyring```

## Remote Desktop from Windows 10
```sh
sudo apt install xrdp
sudo systemctl enable --now xrdp
sudo ufw allow from any to any port 3389 proto tcp
# IP show
ifconfig -a
```

## Browser
### Fast is a factor!
Thorium, I choose you: ```https://github.com/Alex313031/thorium```
<br>
```
Create desktop file
Exec=<path> --password-store=basic
Done! No need to type passwd anymore.
```
<br>
Logo: 

```
https://github.com/Alex313031/thorium/blob/main/logos/NEW/product_logo_2048.png
```

### Quality of Life.
uBlock Origin: ```https://github.com/gorhill/uBlock```
<br>
Youtube Auto Skip Sponsor: ```https://github.com/ajayyy/SponsorBlock```
<br>
Youtube Non Stop: ```https://github.com/lawfx/YoutubeNonStop```
<br>
I am Japanophile: ```https://github.com/FooSoft/yomichan``` && ```https://learnjapanese.link/dictionarie```

## Video player
Always go with MPV, because I love mining sentences: ```https://github.com/mpv-player/mpv```

## E-Learning
Using Anki, it'll help you deal with ADHD: ```https://apps.ankiweb.net/```

## Hakuneko
Manga & Anime Downloader for Linux: ```https://github.com/manga-download/hakuneko```

## Blender
```https://www.blender.org/```

## Python
3.6
```
sudo apt-get update
sudo apt-get install python3.6
```
3.8
```
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt-get update
sudo apt-get install python3.8
```

## Japanese OCR
The best, reliable one: ```https://github.com/blueaxis/Cloe``` && ```https://github.com/kha-white/manga-ocr```

## Using Window Software
I drink Wine:
```sh
sudo dpkg --add-architecture i386
sudo mkdir -pm755 /etc/apt/keyrings
sudo wget -O /etc/apt/keyrings/winehq-archive.key https://dl.winehq.org/wine-builds/winehq.key
sudo wget -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/ubuntu/dists/jammy/winehq-jammy.sources
sudo wget -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/ubuntu/dists/kinetic/winehq-kinetic.sources
sudo apt update && sudo apt install --install-recommends winehq-stable
```
<br>
Play On Linux:

```
https://www.playonlinux.com/en/
```

## ibus-bamboo
### Hello everyone = Dit me may in Vietnamese.
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
On login run: ```Session And Startup```

## Plank
### Love something look like expensive.
```sh
sudo apt update
sudo apt install plank
plank
```
On login run: ```Session And Startup```
