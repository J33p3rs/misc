# OpenCanary
This outlines how to install and configure OpenCanary on a Pi3.

## Prepare the Pi
Use instructions here up to *OpenCanary Installation*
https://bobmckay.com/i-t-support-networking/hardware/create-a-security-honey-pot-with-opencanary-and-a-raspberry-pi-3-updated-2021/

## Install prerequisites and OpenCanary
Follow installl instructions here: https://github.com/thinkst/opencanary for Ubuntu.

## Configure Open Canary
### Move SSH Port
Get a list of least common ports from nmap, pick one of these to migrate your managment SSH to maybe?
```
cd /usr/share/nmap
grep unknown nmap-services | awk -F" " '{print $3 " " $2}' | sort | head
```
### Configure Services
* Copy config file
* Edit config file




