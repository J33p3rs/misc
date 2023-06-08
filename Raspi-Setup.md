# Raspberry Pi setup
Teh following are general items you may wish to configure on any Raspberry Pi set up.

## Regenerate SSH Key
You may wish to regenerate your SSH Key
```
sudo rm /etc/ssh/ssh_host*
sudo ssh-keygen -A
```
## Change the default password
If you are logged in as the user you wiish to change the password for:
```
passwd
```
# And add a non root user

`sudo adduser bob`

## Enable SSH
from: https://www.raspberrypi.org/documentation/remote-access/ssh

As of the November 2016 release, Raspbian has the SSH server disabled by default. It can be enabled manually from the desktop:

Launch Raspberry Pi Configuration from the Preferences menu
* Navigate to the Interfaces tab
* Select Enabled next to SSH
* Click OK

Alternatively, raspi-config can be used in the terminal:
* Enter `sudo raspi-config` in a terminal window
* Select Interfacing Options
* Navigate to and select SSH
* Choose Yes
* Select Ok
* Choose Finish

Alternatively, use systemctl to start the service
* `sudo systemctl enable ssh`
* `sudo systemctl start ssh``

### Headless SSH
If you want to run headless, PRIOR to first boot do the following:
from: https://www.raspberrypi.org/documentation/remote-access/ssh/README.md
>3. Enable SSH on a headless Raspberry Pi (add file to SD card on another machine)
>For headless setup, SSH can be enabled by placing a file named ssh, without any extension, onto the boot partition of the SD 
>card from another computer. When the Pi boots, it looks for the ssh file. If it is found, SSH is enabled and the file is deleted. 
>The content of the file does not matter; it could contain text, or nothing at all.
>
>If you have loaded Raspbian onto a blank SD card, you will have two partitions. The first one, which is the smaller one, is the boot 
>partition. Place the file into this one.

## Set a static IP
From: https://www.tomshardware.com/how-to/static-ip-raspberry-pi

You will need to edit `/etc/dhcpcd.conf`

```
interface [INTERFACE]
static_routers=[ROUTER IP]
static domain_name_servers=[DNS IP]
static ip_address=[STATIC IP ADDRESS YOU WANT]/24
```

To get the details for the above
* `ip r` will show you the interface and router ip (after default via)
* `grep "namesever" /etc/resolv.conf` will give you the name servers
* pick the address you want or use the one you have whioch you can get with `ifconfig`
