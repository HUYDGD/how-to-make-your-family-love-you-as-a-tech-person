# How To Make Your Family Love You As A Tech Person
In the past, I made a mistake by buying an "Android TV box". That was a few years ago, and its specifications can't even play a YouTube video. So I decide to build a new PC and choose Linux as the OS for watching TV, surfing the web and learning. This repository is a synthesis of what a Linux system would be like! I choose XFCE as DE because it's light but if you have a decent PC specs you can choose any distros you like!
<br>
This github includes everything you want to do on a fresh Linux system, it's different depending on your hardware and your distro you use. So always do your research on the internet. If you choose XFCE (Xubuntu, Linux Mint, Debian,..) like me, things will be easier for you because it's work for me.

# Installation

## Distros
Best USB bootable: ```https://github.com/ventoy/Ventoy```

## Check Disks
I buy cheap stuff from Taobao, so always be careful.
<br>
```sh
sudo apt-get install gsmartcontrol
sudo gsmartcontrol
```
## Disk Permission
All users: ```sudo chmod 777 <foldername>```
<br>
Specific user:
```sh
mkdir <your folder name> #sudo might be needed.
sudo chown user:user <folder name>
sudo chmod 770 <folder name>  #user and sudoers full access, other no access
```

## RAID
Original post: ```https://www.computernetworkingnotes.com/linux-tutorials/how-to-configure-raid-in-linux-step-by-step-guide.html```
<br>
Choose RAID 1 or RAID 5 for better safe.
```sh
sudo apt install mdadm
sudo mdadm --create --verbose /dev/[ RAID array Name or Number] --level=[RAID Level] --raid-devices=[Number of storage devices] [Storage Device] [Storage Device]
mkfs –t [File system type] [RAID Device]
#RAID 0 with 3 drives
sudo mdadm --create --verbose /dev/md0 --level=0 --raid-devices=3 /dev/sdb /dev/sdc /dev/sdd
mkfs –t ext4 /dev/md0
```

# Wifi & Ethernet & Bluetooth
```sh
iwconfig # See all devices
sudo ifconfig <device> up # Enable

# Bluetooth
sudo systemctl enable bluetooth.service
sudo systemctl start bluetooth.service
rfkill # Check status
sudo rfkill unblock bluetooth
```

## Audio 
```sh
sudo apt-get install pavucontrol
pavucontrol
```

## Set Default Microphone
```sh
pactl list short sources
pactl set-default-source <name>
```

# Fix Microphone Not Working
```sh
arecord --duration=5 --format=dat test-mic.wav
aplay test-mic.wav
```

## Set Default Audio Output Device
```sh
pactl list short sinks
pactl set-default-sink 'Your_Device_Name'
```

## Change Audio Bitrate
```sh
sudo nano /etc/pulse/daemon.conf
flat-volumes = no   
resample-method = speex-float-3
default-sample-format = s24le
default-sample-rate = 192000
```

## Disable gnome-keyring
Parents shouldn't waste time with technology, all they need is fast and quality.
<br>
```sudo apt-get remove gnome-keyring```
```sudo apt install seahorse```

## Disable Lock Screen
It's so annoying me when playing game, so I decide to disable this feature.
```sh
if below command gives false then set it to true

gsettings get org.gnome.desktop.lockdown disable-lock-screen
gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'
if below command returns true then set it false

gsettings get org.gnome.desktop.screensaver lock-enabled
gsettings set org.gnome.desktop.screensaver lock-enabled false
if below command returns true then set it false

gsettings get org.gnome.desktop.screensaver idle-activation-enabled
gsettings set org.gnome.desktop.screensaver idle-activation-enabled false
```
```sh
gsettings set org.gnome.desktop.lockdown disable-lock-screen true
gsettings set org.gnome.desktop.screensaver lock-enabled false
gsettings set org.gnome.desktop.screensaver ubuntu-lock-on-suspend false
gsettings set org.gnome.desktop.screensaver idle-activation-enabled false
gsettings set org.gnome.desktop.session idle-delay 0
```
```sh
Screensaver -> Disable screen saver
```

## Logout User
```
sudo pkill -SIGKIL -u <user>
```

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

Logo: ```https://github.com/Alex313031/thorium/blob/main/logos/NEW/product_logo_2048.png```

### Quality of Life.
uBlock Origin: ```https://github.com/gorhill/uBlock```
<br>
Youtube Auto Skip Sponsor: ```https://github.com/ajayyy/SponsorBlock```
<br>
Youtube Non Stop: ```https://github.com/lawfx/YoutubeNonStop```
<br>
I am Japanophile: ```https://github.com/FooSoft/yomichan``` && ```https://learnjapanese.link/dictionarie```

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
1. Change display cable (HDMI, VGA, DVI,...)
(Work for me, it's decrease the amount of lagging)
2. Remove graphic drivers
3. Allow more ram for integrated GPU in BIOS setting. I use GA-B85-HD3, after change the value to 1024M for my iGPU, the issue is gone.
4. Disable compositors (maybe)
5. In my case, I don't use propriety drivers, just use X Server instead. The problem will be fixed.
The issue is always related to cable or graphic card. AMD is your friend when choosing hardware for Linux!
6. sudo add-apt-repository ppa:graphics-drivers/ppa && sudo dpkg --add-architecture i386 && sudo apt update && sudo apt install -y nvidia-driver-535 libvulkan1 libvulkan1:i386
7. sudo add-apt-repository ppa:kisak/kisak-mesa && sudo dpkg --add-architecture i386 && sudo apt update && sudo apt upgrade && sudo apt install libgl1-mesa-dri:i386 mesa-vulkan-drivers mesa-vulkan-drivers:i386
8. nvidia-settings -a "[gpu:0]/GpuPowerMizerMode=1"
```
More links.
```https://github.com/bauca/graphics-switcher```
```https://forums.developer.nvidia.com/t/for-those-having-stutters-under-x11/265708```
```https://forums.linuxmint.com/viewtopic.php?t=360334```
```https://askubuntu.com/questions/1230768/stutter-every-500-ms-using-nvidia-driver```
```https://www.google.com/search?q=nvidia+drivers+stutter+linux&oq=nvidia+drivers+stutter+linux```

## NVIDIA Fail On Boot
```sh
xed admin:///etc/modules
nvidia 
nvidia-drm
nvidia-modeset
sudo update-initramfs -u
```

## NVIDIA Drivers Uninstall
```sh
sudo nvidia-uninstall
sudo apt remove nvidia-*
sudo apt-get remove --purge nvidia-*
sudo apt-get remove --purge libnvidia-*
sudo ubuntu-drivers autoinstall
sudo apt autoremove
sudo apt autoclean
```

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

## OCR Japanese with Cloe
Cloe is the best OCR ever! It's use manga-ocr.
```https://github.com/blueaxis/Cloe```
```sh
sudo apt-get install python3-pyqt5
sudo apt-get install python3-pip
sudo pip install pynput
sudo pip3 install manga-ocr
python3 main.py
```
How to fix bug small window on Linux:

```sh
cd ./app/components/views/ocr
sudo nano base.py
```

```sh
class BaseOCRView(QGraphicsView):
    """
    Base view with OCR capabilities
    """

    def __init__(self, parent: QWidget):
        super().__init__(parent)
        self.setMinimumSize(QSize(1360,768)) #Change size to match your windows size!
        self._timer = QTimer()
        self._timer.setInterval(300)
        self._timer.setSingleShot(True)
        self._timer.timeout.connect(self.rubberBandStopped)
```

## Video player
Always go with MPV, because I love mining sentences: ```https://github.com/mpv-player/mpv```

## E-Learning
Using Anki, it'll help you deal with ADHD: ```https://apps.ankiweb.net/```

## Fix Anki Blank
```sh
.bashrc
alias anki="QTWEBENGINE_DISABLE_SANDBOX=1 anki"
```

## Reading E-Books (PDF, MOBI, EPUB,...)
```https://github.com/kovidgoyal/calibre```

## Hakuneko
Manga & Anime Downloader for Linux: ```https://github.com/manga-download/hakuneko```

## Blender
```https://www.blender.org/```

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
sudo apt-get install winetricks
```
<br>
Play On Linux:

```
https://www.playonlinux.com/en/
```

## Gaming with Lutris
```https://github.com/lutris/lutris```
```https://github.com/lutris/docs```

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

## Install Compton
Compton is a standalone lightweight compositor for X (the graphic server on Linux systems). It provides 2D graphical acceleration and this allow us to drop shadows under the windows, make elements fade as they (dis)appear, draw (semi)transparent menus and notifications, etc.
```
sudo apt-get install -y compton
```

## Lazy Sofa With A Joystick Controller
My house has a sofa, parents just get older, they shouldn't sit in the chair and stare in a big screen. That's cause health problem!
<br>
Using this software, you can plug in any device like a controller, gamepad. You can map any keyboard to that device. Feel free using computer while laying the bed!
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


