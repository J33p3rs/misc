# OpenCanary
This outlines how to install and configure OpenCanary on a Pi3.

## Prepare the Pi
Use instructions here up to *OpenCanary Installation*
https://bobmckay.com/i-t-support-networking/hardware/create-a-security-honey-pot-with-opencanary-and-a-raspberry-pi-3-updated-2021/

## Install prerequisites and OpenCanary
Follow installl instructions here: https://github.com/thinkst/opencanary for Ubuntu.

>**Note** As we are only using the pi for opencanary there is not a need to build it in a venv. Although this helps managing dependencies a little easier.

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

### Making it Autostart -- cron

For the pi it is best to edit this via vi /etc/crontab rather than crontab -e

````
### OpenCanary start ###
# Start OpenCanary every 5 mins, this way if it fails, it gets started again.
# (Bit of a hack until I get systemctl working)

# Start every 5 mins
5 * * * * pi opencanaryd --start

```

### Making it Autostart - systemctl attempt
> After a bit of work I ended up giving up on the systemctl approach.
>
> Most likely it is related to the following:
> `journalctl _SYSTEMD_UNIT=opencanary.service`
>
> `Traceback (most recent call last):`
> `File "/home/jp/.local/bin/twistd", line 5, in <module>`
> `from twisted.scripts.twistd import run`
> `ModuleNotFoundError: No module named 'twisted'`

*I'll elave it hhere for future regerence*

From: https://bobmckay.com/i-t-support-networking/hardware/create-a-security-honey-pot-with-opencanary-and-a-raspberry-pi-3-updated-2021/

In order to have OpenCanary service automatically start on boot up, we need to create a systemd file for it:

`sudo nano /etc/systemd/system/opencanary.service`

Then give it a configuration (note the oneshot config item is removed in the below, that was on the OpenCanary instruuctions. Also, you will need ot replace the `<VIRTUAL_ENV_PATH>` with the path to your configuration, maybe `/home/pi/.local`? :
```
[Unit]
Description=OpenCanary
After=syslog.target
After=network-online.target

[Service]
User=root
RemainAfterExit=yes
Restart=always
ExecStart=<VIRTUAL_ENV_PATH>/bin/opencanaryd --start
ExecStop=<VIRTUAL_ENV_PATH>/bin/opencanaryd --stop

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
| Colby's Honeypot workshop | https://github.com/colbyprior/honeypot-workshop/tree/master |
| Some other Canary things to try | https://github.com/sudosammy/knary <br> https://github.com/intelowlproject/IntelOwl |



