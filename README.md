# huydgd-xubuntu-config
HUYDGD Xubuntu Config. Goal is a fastest desktop use for family watching TV and e-learning.

# Installation

## Check Disks
I buy cheap stuff from Taobao, so always be careful.
<br>
```sh
sudo apt-get install gsmartcontrol
sudo gsmartcontrol
```
## RAID
```sh
sudo apt install mdadm
mdadm --create --verbose /dev/[ RAID array Name or Number] --level=[RAID Level] --raid-devices=[Number of storage devices] [Storage Device] [Storage Device]
```

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

## Type Telex with ibus-bamboo
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

## Look Like MacOS with Plank
### Love something look like expensive.
```sh
sudo apt update
sudo apt install plank
plank
```
On login run: ```Session And Startup```

## Fix Screen Choppy, Tearing, Stutter, Lagging
```sh
Try this steps if one of these working! I'm using Intel i3-4130 and NVIDIA Geforce GT 730.
1. Change display cable (HDMI< VGA< DVI,...)
(Work for me, it's decrease the amount of lagging)
2. Remove graphic drivers
3. Allow more ram for integrated GPU in BIOS setting. I use GA-B85-HD3, after change the value to 1024M for my iGPU, the issue is gone.
4. Disable compositors (maybe)
The issue is always related to cable or graphic card. AMD is your friend when choosing hardware for Linux!
```

## Lazy Sofa
My house has a sofa, parents just get older, they shouldn't sit in the chair and stare in a big screen. That's cause health problem!
<br>
Using this software, you can plug in any device like a controller, gamepad. You can map any keyboard to that device. Feel free using computer while laying the bed!
<br>
AntiMicro: ```https://github.com/AntiMicro/antimicro```
<br>
AntiMicroX (Install this, new version): ```https://github.com/AntiMicroX/antimicrox```
<br>
If you have a bluetooth card, life will be easier!

## Edit Family Video
I'm learning how to use it right now to teach my mom to edit her video. She can say goodbye to Capcut & Kinemaster again!
<br>
Davinci Resolve (It's free): ```https://www.blackmagicdesign.com/products/davinciresolve```

## Edit Family Photo
Never used GIMP before, but I'm decide to learn it!
<br>
GIMP: ```https://www.gimp.org/```

## Livestream and Karaoke
My mom want to share her song through social media, you can install OBS to do that.
<br>
OBS: ```https://obsproject.com/```


