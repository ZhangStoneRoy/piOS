# Custom Pi OS
My astrophotography Raspberry Pi setup. Only Markdown guide right now.
## APT Config
```
wget -O - https://www.astroberry.io/repo/key | sudo apt-key add -
sudo su -c "echo 'deb https://www.astroberry.io/repo/ buster main' > /etc/apt/sources.list.d/astroberry.list"
wget -O - https://ppa.stellarmate.com/repos/apt/conf/sm.gpg.key | sudo apt-key add -
sudo su -c "echo 'deb http://ppa.stellarmate.com/repos/apt/stable buster main' > /etc/apt/sources.list.d/stellarmate.list"
sudo apt update
sudo apt upgrade
```
## Install Packages
```
sudo apt -y install kstars-bleeding indi-full libindi-dev gsc ser-player virtualgps gpsd-clients indiwebmanagerapp chrony filezilla libopencv-imgproc3.2
#wget https://www.qhyccd.com/uploadfile/2018/1222/20181222054634222.zip
#unzip 20181222054634222.zip | sudo dpkg -i -
sudo ln -s /usr/lib/arm-linux-gnueabihf/libqhyccd.so /usr/lib/arm-linux-gnueabihf/libqhyccd.so.4 && sudo ln -s /usr/lib/arm-linux-gnueabihf/libopencv_imgproc.so.3.2 /usr/lib/arm-linux-gnueabihf/libopencv_imgproc.so.2.4 && sudo ln -s /usr/lib/arm-linux-gnueabihf/libopencv_core.so.3.2 /usr/lib/arm-linux-gnueabihf/libopencv_core.so.2.4
```
*oacapture cannot be installed due to dependency issue w/ KStars.*
*PoleMaster file is in NAS*
Add this to .bashrc:
```
export PATH=$PATH:/usr/bin/PoleMaster
alias sudo='sudo env PATH=$PATH'
```
**Change System Manu shortcut to `sudo /usr/bin/PoleMaster/PoleMaster`**
## Setup System
1. Setup using `sudo raspi-config`
--Localisazion
--Resolution
--etc.
2. Wifi
```
mkdir Projects && cd Projects
git clone https://github.com/unixabg/RPI-Wireless-Hotspot.git
```
cd, `sudo ./install`
3. Setup VirtualGPS
```
sudo systemctl enable virtualgps && sudo systemctl start virtualgps
sudo nano /etc/location.conf
```
> 39.925, 116.433
4. For GPS setup chrony and use gps module /dev/ttyS0
follow https://www.waveshare.net/wiki/L76X_GPS_Module
and https://gpsd.gitlab.io/gpsd/gpsd-time-service-howto.html

## Setup KStars
~~whatever~~
