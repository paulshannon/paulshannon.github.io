---
layout: post
title: Raspberry Pi as Digital Signage
published: True
categories: []
tags: pi, linux, signage
---

1. [Set to boot into desktop](http://www.raspberrypi.org/documentation/configuration/raspi-config.md)

	```
	sudo raspi-config
	```

2. [Setup timezone](http://www.raspberrypi.org/forums/viewtopic.php?f=26&t=10291)

	```
	sudo dpkg-reconfigure tzdata
	```

3. [Setup to boot to browser](http://www.niteoweb.com/blog/raspberry-pi-boot-to-browser)

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
