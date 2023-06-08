# Pihole on Pi Zero W
This was a session  run by Toowoomba Sectalks (0x01)
## Overview of process
* Install Rasperry Pi OS (If using Rasperry Pi Imager this can be done within settings via cog)
  * Setup wpa_supplicant.conf
  * Create blank ssh file
* Boot pi
* Set static IP if wanted
* Install pihole
  * Use bash script from pihoile repo
* Add block lists
  * SANS Blocklists 
* Update default passwords etc
* Create cronjobs to update pihole, update gravity and reboot
* Cut over from existing DNS provider (e.g., home router config change)

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
## Set Static IP
https://github.com/J33p3rs/misc/blob/main/Raspi-Setup.md

## Crontab
For the pi it is best to edit this via `vi /etc/crontab` rather than `crontab -e`

```
### Pihole Backup ###
# Backup Pi-hole configuration (settings & lists) as a downloadable archive

# Daily Backup at 23:15 every day
15 23 * * * pi pihole -a -t ~/backup/backup_daily

# Weekly backup at 23:30 every Monday
30 23 * * 1 pi pihole -a -t ~/backup/backup_weekly

# Monthly backup at 23:45 on the 1st of each month
45 23 1 * * pi pihole -a -t ~/backup/backup_monthly

### Updates ###

# Update apt package index at midnight every day.
0 0 * * * pi sudo apt update

# Update Pi-hole to latest at 01:00am every day
0 1 * * * pi pihole -up

# Upgrade Raspberry Pi OS every week at 02:00am on Mondays

0 2 * * 1 pi sudo apt upgrade -y

# Update Gravity (Pi-hole block lists) every 4 hours, at 50 mins past the hour.
50 */4 * * * pi pihole -g

```
## Resources
| Resoruce | Link | 
| --- | --- | 
| How to | https://medium.com/swlh/how-to-set-up-pi-hole-2293246dc8ed| 
| SANS Internet Storm Centre Diary re: pihoile blocklists | https://handlers.sans.edu/gbruneau/pihole.htm |

