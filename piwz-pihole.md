# Pihole on Pi Zero W
This was a session  run by Toowoomba Sectalks (0x01)
## Overview of process
* Install Rasperry Pi OS (If using Rasperry Pi Imager this can be done within settings via cog)
  * Setup wpa_supplicant.conf
  * Create blank ssh file
* Boot pi
* Install pihole
  * Use bash script from pihoile repo
* Add block lists
  * SANS Blocklists 
* Update default passwords etc
* Create cronjobs to update pihole, update gravity and reboot

### WPA_supplicant.conf
This file can be done automatically when the SD Card is imaged using **Raspberry Pi Imager** and selecting the settings cog before writing the image.

To complete manually, perform tthe following.

From: https://www.raspberrypi-spy.co.uk/2017/04/manually-setting-up-pi-wifi-using-wpa_supplicant-conf/
```
country=us
update_config=1
ctrl_interface=/var/run/wpa_supplicant

network={
 scan_ssid=1
 ssid="MyNetworkSSID"
 psk="Pa55w0rd1234"
}
```
## Resources
| Resoruce | Link | 
| --- | --- | 
| How to | https://medium.com/swlh/how-to-set-up-pi-hole-2293246dc8ed| 
| SANS Internet Storm Centre Diary re: pihoile blocklists | https://handlers.sans.edu/gbruneau/pihole.htm |

