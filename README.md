# Raspberry Pi development setup

Setup instruction to get RPi ready for development. Some crazy things which kills time before getting to business.

## First thing to do
```
  sudo apt-get update
  sudo apt-get install vim
```

## Enable SSH for remote login

* Fist login to rpi using display and keyboard attached to rpi board.

```
  sudo rm /var/log/regen_ssh_keys.log 
  sudo rm /etc/ssh/ssh_host*
  sudo ssh-keygen -A
  sudo raspi-config
```
* Enable ssh from config advance settings.
* Reboot device
```
  sudo reboot
```
After RPi has rebooted. Login to device remotely. Below command is for login from Ubuntu.

```
  ssh pi@192.168.0.100
      raspberry
```
Second time onwards you can provide password in line, if you are not sceptic about the password hacked :). Otherwise create alias of this one line in your bash script and access.
```
sshpass -p raspberry ssh pi@192.168.0.104
```

## Making RPi wireless

```
sudo vi /etc/wpa_supplicant/wpa_supplicant.conf
```
Add below configuration entry by replacing with your own SSID and password

```
network={
    ssid="The_ESSID_from_earlier"
    psk="Your_wifi_password"
}
```
And reboot the device for best:
```
sudo reboot
```

# To work on NodeJS

## Install NPM

There are different approach to install npm but the one which is most convenient
```
wget https://www.npmjs.com/install.sh && chmod a+x ./install.sh && sudo ./install.sh
```
More installation options can be seen at https://github.com/npm/npm

## Install any package to Node-RED
Below is an example of installing additional package in Node-RED. Change with package name you want to install.
```
cd ~/.node-red/node_modules
npm install node-red-contrib-sitewhere
```

