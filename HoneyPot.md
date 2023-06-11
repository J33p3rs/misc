# OpenCanary
This outlines how to install and configure OpenCanary on a Pi3.

## Prepare the Pi
Use instructions here up to *OpenCanary Installation*
https://bobmckay.com/i-t-support-networking/hardware/create-a-security-honey-pot-with-opencanary-and-a-raspberry-pi-3-updated-2021/

## Install prerequisites and OpenCanary
Follow installl instructions here: https://github.com/thinkst/opencanary for Ubuntu.

>**Note** As we are only using the pi for opencanary there is not a need to build it in a venv.

## Configure Open Canary
### Move SSH Port
Get a list of least common ports from nmap, pick one of these to migrate your managment SSH to maybe?
```
cd /usr/share/nmap
grep unknown nmap-services | awk -F" " '{print $3 " " $2}' | sort | head
```
Edit sshd_config:
`sudo nano /etc/ssh/sshd_config`

Find `#Port 22` and uncomment it, and add the port you wish to use.


### Configure Services
* Copy config file
* Edit config file


### Making it Autostart
From: https://bobmckay.com/i-t-support-networking/hardware/create-a-security-honey-pot-with-opencanary-and-a-raspberry-pi-3-updated-2021/

In order to have OpenCanary service automatically start on boot up, we need to create a systemd file for it:

`sudo nano /etc/systemd/system/opencanary.service`

Then give it a configuration:
```
[Unit]
Description=OpenCanary
After=syslog.target
After=network.target

[Service]
User=root
Restart=always
WorkingDirectory=/home/pi/opencanary
ExecStart=/home/pi/opencanary/bin/opencanaryd --dev

[Install]
WantedBy=multi-user.target
```
Now we need to enable the service:
```
sudo systemctl enable opencanary.service
sudo systemctl start opencanary.service
```
We can check the service status by running:

`systemctl status opencanary.service`

## References
| Type | Link |
| --- | --- | 
| Config examples | <li> https://bobmckay.com/i-t-support-networking/hardware/create-a-security-honey-pot-with-opencanary-and-a-raspberry-pi-3-updated-2021/ <br><li> https://medium.com/@nahberry/opencanary-on-a-raspberry-pi-528242fcb3dd <br><li> https://opencanary.readthedocs.io/en/latest/starting/configuration.html |




