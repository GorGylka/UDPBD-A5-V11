![img_photo]
<h2 align="left">OpenWRT UDPBD for A5-V11 3G/4G Mini Router</h2>

<h3 align="left">Features:</h3>  

- Blazing 4.2mb/s speed   
- exFAT Support  
- external HDD, SSD, USB Drives up to 2TB  
- Lower power consumption by 45% ( No more overheating ( heatsink still recommended ) )


<img src="https://github.com/GorGylka/UDPBD-A5-V11/blob/main/compare.jpg" width=70% height=70%>
<img src="https://github.com/GorGylka/UDPBD-A5-V11/blob/main/Speed.jpg">
<h3 align="left">You will need:</h3>

- A5-V11 3G/4G (You must have 4MB Flash / 32MB RAM)  
- USB Drive in Fat32 (to flash Router once)  
- USB Drive in exFAT (to run backups)  

<h3 align="left">Router:</h3>

-Transfer ```lede-ramips-rt305x-a5-v11-squashfs-sysupgrade.bin``` and ```uboot_usb_256_03.img``` to a root FAT32 flash drive  
-Install [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)  
-Plug Router to PC, connect via Putty with these connection settings: ```192.168.100.1``` / ```23``` / ```Telnet```, press ```Connect```  
<img src="https://github.com/GorGylka/UDPBD-A5-V11/blob/main/1.jpg" width=50% height=50%>  
-Login ```admin```, Password ```admin```  
-Type comands, 1 by 1:  
```
ls /media/sda1/
```
```
mtd_write write /media/sda1/uboot_usb_256_03.img Bootloader
```
```
mtd_write write /media/sda1/lede-ramips-rt305x-a5-v11-squashfs-sysupgrade.bin Kernel
```
```
reboot
```
Correct output:  
<img src="https://github.com/GorGylka/UDPBD-A5-V11/blob/main/2.jpg" width=50% height=50%>  
-Open Browser ```192.168.1.1```  
(it take about 2 min to reboot)  
-```Login```(no password) --> ```Go to Password Configuraion``` --> Password ```admin``` --> Confirmation ```admin``` --> interface ```LAN``` --> ```Save and Apply```  
<img src="https://github.com/GorGylka/UDPBD-A5-V11/blob/main/4.jpg" width=50% height=50%>  
-Disconnect micro usb from Router, eject FAT32 USB, inject exFAT USB, connect micro usb  
-Go to ```192.168.1.1```, Log in, ```System``` --> ```Mount Points``` --> check that your exFAT USB drive is detected on ```/dev/sda1```  
<img src="https://github.com/GorGylka/UDPBD-A5-V11/blob/main/5.jpg" width=50% height=50%>  
-Router is Done!  


<h3 align="left">USB Drive:</h3>

-Format USB to GUID Partition Table (GPT), exFat, Standart Cluster Size  
(I highly recommend using [GParted Live USB](https://gparted.org/liveusb.php) over Windows formatting)  
-Do standart USB config for PS2 (create CD/DVD folders, add backups, ARTs, e.t.c.)

<h3 align="left">PS2:</h3>

-Place [OPNPS2LD-v1.2.0-Beta-1973-88079d7-UDPBD.elf](https://github.com/GorGylka/UDPBD-A5-V11/releases/) into bootable memory card  
-Delete/archive opl .cfg files, there are stored in:  
mc0:/OPL/conf_network.cfg  
mc0:/OPL/conf_opl.cfg  
-Make this version of OPL apperable on FMCB/Funtuna menu or config to autoboot this version of OPL  
-Remove any USB Drive from PS2 (important!)  
-Connect power to the router, having first connected the LAN to PS2 and USB Drive to Router  
-Run OPNPS2LD..UDPBD.elf  
Settings->BDM Start Mode->Manual  
Settings->Default Menu->BDM Games->OK->Save Changes  

<h3 align="left">Notes:</h3>

-Router take some time to start and init. I didn't time it exactly, please wait 2 minutes in FMCB Menu or press Start ->Exit -> (run OPL again)  

-I disable WiFi and disable unsoldered LANs to reduce power consumption, but it still strongly recommend:  
 - Heatsink on Ralink Chip 

<img src="https://github.com/GorGylka/UDPBD-A5-V11/blob/main/heatsink.jpg" width=30% height=30%>
 
 - Hardmod MAX809TTR / ADM809 (Router doesn't always turn on after hard reboot without it)  

<img src="https://github.com/GorGylka/UDPBD-A5-V11/blob/main/max809ttr.jpg" width=30% height=30%>

-If you don't see the list of games, first try setting up UDPBD with configured USB on your PC  
-System does not have Plug-and-play feature. inject USB Drive before power on and eject after power off.  


[img_photo]: https://github.com/GorGylka/UDPBD-A5-V11/blob/main/logo.jpg
