---
layout: post
title: Raspberry Pi as Digital Signage
published: True
categories: []
tags: pi, linux, signage
---

I've setup some digital signage using a very simple django app and a webpage that displays rotating advertisements for upcoming events as well as news headlines and the current time. We're switching over to running the displays over some [Raspberry Pis](http://www.raspberrypi.org/) and this is how I configured them:

1. [Set to boot into desktop](http://www.raspberrypi.org/documentation/configuration/raspi-config.md)

	```
	sudo raspi-config
	```

2. [Setup timezone](http://www.raspberrypi.org/forums/viewtopic.php?f=26&t=10291)

	```
	sudo dpkg-reconfigure tzdata
	```

3. [Setup to boot to fullscreen browser](http://www.niteoweb.com/blog/raspberry-pi-boot-to-browser)

	Disable screen sleep -- so the screen stays on
		
		$ sudo nano /etc/lightdm/lightdm.conf

		# add the following lines to the [SeatDefaults] section
		
		# don't sleep the screen
		xserver-command=X -s 0 dpms
		

	Hide cursor on inactivity
		
		$ sudo apt-get install unclutter
		
	Configure LXDE to start the Midori browser on login

		$ sudo nano /etc/xdg/lxsession/LXDE/autostart 

		# comment everything and add the following lines

		@xset s off
		@xset -dpms
		@xset s noblank
		@midori -e Fullscreen -a <Website to open>

4. Change password for default user

	```
	passwd
	```

5. [Force Resolution](http://weblogs.asp.net/bleroy/getting-your-raspberry-pi-to-output-the-right-resolution)

	1. Get the list of what’s supported by your monitor:

		tvservice -d edid
		edidparser edid

	2. Find the mode that you want in the resulting list. The mode number is the one between parentheses.

	3. Edit the config file:

		sudo nano /boot/config.txt

		hdmi_group=2
		hdmi_mode=<mode>

	4. Reboot:

		sudo reboot
	