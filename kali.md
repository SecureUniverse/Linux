# KALI

## Add VPN
```apt install network-manager-openconnect-gnome```

Setting -> Network -> Add VPN -> Multi-protocol VPN client(openconnect)
- Gateway: s30.speedserver.info:555
- Enter User/Pass
  - http://www.speed-vpn.com
  - http://buyspvp5.xyz

## Tor Browser
Download from ![TorBrowser](https://www.torproject.org/download/)

Login with root user
```
sudo adduser toruser
tar -xf tor-browser-linux64-9.0.4_en-US.tar.xz
./start-tor-browser.desktop
```

## Mount USB

Show device: ```lsblk```

Create directory: ```sudo mkdir /media/usbstick```

Mount: 
```
sudo mount -t vfat /dev/sdb1 /media/usbstick
sudo mount -t ntfs-3g /dev/sdb1 /media/usb
```

## Create Non-Root User
```
useradd -m brian -G sudo -s /bin/bash
passwd brian
```

## Change SSH port
```
netstat -tnlp
service ssh stop
nano /etc/ssh/sshd_config
service ssh start
netstat -tnlp
```
