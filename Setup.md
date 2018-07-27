# SETTING UP A HEADLESS RASPBERRY PI


##Requirements for these processes:
1. A raspberry Pi 3
2. Etcher
3. Latest Raspberry Pi operating system
4. Ubuntu Laptop


##Procedure.

1. Insert the SD card you intend to use for the Raspberry Pi into the laptop running ubuntu
2. Run Etcher by double clicking on the “.run” file
3. Following the dialog and flash the Sd card with the latest raspbian operating system
4. When the flashing completes, go to your file manager and locate the “/boot/” partition
5. You will need to activate ssh and also setup your raspberry pi to connect to the internet. The next steps will guide you to do that
6. Open your terminal on ubunt and navigate to the boot partition it usually will be located at ‘/media/<username>/boot’
7. Create an ssh file (without extensions) by running:
>> sudo touch ssh
8. This file instructs the raspberry pi on bootup to enable ssh
9. Next is to create a wpa_supplicant.conf file which will be used to setup the raspberry pi to connect to the internet
10. Run the command:
>> sudo nano wpa_supplicant.conf


11. A blank file will open and you should type the following:
	ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
	update_config=1
	country=<< your ISO-3166_two-letter_country_code>>
	network={
			ssid=”<<your SSID>>”
			psk=”<<your _PSK>>”
			key_mgmt=WPA-PSK
	}

12. Replace your <<your ISO-3166-1_two-letter_country_code>> with your ISO Country Code; for nigeria that is NG.

13. When you have filled in the information hit Ctrl+X to save and pres Y and enter

14. Unmount your boot partition using the file manager and insert the SD card into your raspberrypi

15. Make sure that your network hotspot is on and that your PC is connected to the same network

16. Power on your Raspberry Pi.

17. On your ubuntu PC open a terminal and run the following command to obtain the raspberry pi ipaddress.

>> ping -c 1 raspberrypi.local
This will gie you your Raspberry Pi IP address (that -c 1 tells the system to only ping your Pi once, otherwise it’ll just keep going.)

18. With your address you’ll SSH into your system via

>> ssh pi@<<your.ip.address>>

19. Your password will be requested; since this is a new raspberry pi, the default password is <raspberry>. Enter raspberry to log in
20. You will be logged in to your raspberry pi

21. now change your password by running the following command.

>> passwd
A prompt will appear asking you to enter your current password (raspberry) 
and a new password twice.
22. You are now set up to use your raspberry pi through ssh anytime you start it up.

##Key commands to remember are:

1. >> ping -c 1 raspberrypi.local
	this returns the raspberrypi ip address
2. >> ssh pi@<your.ip.address>


