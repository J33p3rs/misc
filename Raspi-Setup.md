# You may wish to regenerate your SSH Key
sudo rm /etc/ssh/ssh_host*
sudo ssh-keygen -A

# And change the default password
passwd

# And add a non root user
sudo adduser bob

# Enable SSH (from: https://www.raspberrypi.org/documentation/remote-access/ssh/)
As of the November 2016 release, Raspbian has the SSH server disabled by default. It can be enabled manually from the desktop:

Launch Raspberry Pi Configuration from the Preferences menu
Navigate to the Interfaces tab
Select Enabled next to SSH
Click OK
Alternatively, raspi-config can be used in the terminal:

Enter sudo raspi-config in a terminal window
Select Interfacing Options
Navigate to and select SSH
Choose Yes
Select Ok
Choose Finish
Alternatively, use systemctl to start the service

sudo systemctl enable ssh
sudo systemctl start ssh

#If you want to run headless, PRIOR to first boot do the following: (from: https://www.raspberrypi.org/documentation/remote-access/ssh/README.md)
3. Enable SSH on a headless Raspberry Pi (add file to SD card on another machine)
For headless setup, SSH can be enabled by placing a file named ssh, without any extension, onto the boot partition of the SD 
card from another computer. When the Pi boots, it looks for the ssh file. If it is found, SSH is enabled and the file is deleted. 
The content of the file does not matter; it could contain text, or nothing at all.

If you have loaded Raspbian onto a blank SD card, you will have two partitions. The first one, which is the smaller one, is the boot 
partition. Place the file into this one.
