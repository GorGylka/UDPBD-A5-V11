
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

<h2 align="left">Router:</h2>  
<h3 align="left">Software Method:</h3>  

-Transfer ```lede-ramips-rt305x-a5-v11-squashfs-sysupgrade.bin``` and ```uboot_usb_256_03.img``` to a root FAT32 USB, plug USB into router  
-Install [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)  
-Plug Router to PC, connect via Putty with these connection settings: ```192.168.100.1``` / ```23``` / ```Telnet```, press ```Connect```  
<img src="https://github.com/GorGylka/UDPBD-A5-V11/blob/main/1.jpg" width=50% height=50%>  
-Login ```admin```, Password ```admin``` (blind input)  
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
<h3 align="left">Hardware Method:</h3> 

-Flash ```OpenWRT_17.01.7_MX25L3205.bin``` via CH341A or any compatible BIOS programmer  
-Router is Done!  

<h2 align="left">USB Drive:</h2>

-Format USB to GUID Partition Table (GPT), exFat, Standart Cluster Size  
(I highly recommend using [GParted Live USB](https://gparted.org/liveusb.php) over Windows formatting)  
-Do standart USB config for PS2 (create CD/DVD folders, add backups, ARTs, e.t.c.)

<h2 align="left">PS2:</h2>

<h3 align="left">1st Method (Using my dump):</h3>  
<h3 align="left">You will need:</h3>

- FAT32 USB Drive
- 8MB MemoryCard (orig or clone, 64mb and more __not supported__)      
- Ability to run ulaunchELF  

-Place ```FMCB-OPENTUNA``` folder into root FAT32 USB Drive, insert into PS2  
-Run uLaunchELF  
-Run mass:/FMCB-OPENTUNA/FMCBInstaller.elf  
Make sure that the correct MC is inserted into PS2 slot 1, slot 2 is empty  
-Restore MC ( Press ```R1``` ```R1``` ```Down``` ```Down``` ```X``` ), Confirm  
(careful, it will format your MemoryCard)  
-Install FMCB Multi-install ( Press ```L1``` ```L1``` ```Down``` ```X``` ), Confirm  
-Exit, Reboot PS2, Eject USB from PS2  

<img src="https://github.com/GorGylka/UDPBD-A5-V11/blob/main/uLE.jpg" width=50% height=50%>

This will install the latest FMCB and OPENTUNA on one card. FMCB automatically launches uLaunchELF, which launches OPL with a perfectly calculated timer to ensure the router has time to boot, if youre power router from PS2 USB. If you have a PS2 90000, or your MC is a clone, you can run the OpenTuna exploit, which then does the same. To open the FMCB menu, hold the triangle while turning on your PS2 until the menu appears.  
This combination of Apps should work on most (if not all) Slim PS2

<h3 align="left">2nd Method (Manual):</h3>  

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

<h3 align="left">3rd Method (PSxMemCard Users):</h3>  

-Place the contents of ```psxmemcard.zip``` in the root of your ```SD2PSX``` / ```PSXMemCard Gen2``` / ```PSXMemCard Gen1``` / ```PicoMemcard+```  

<h2 align="left">Notes:</h2>

-Router take 30 seconds to start and init drive. Please wait 1 minute in FMCB Menu before start OPL or press Start ->Exit -> (run OPL again).  

-You cannot use any other version of OPL, UDPBD works only in this specific version.  

-If USB drive is connected to the PS2 while OPL is running, UDPBD will not start.  

-I disable WiFi and disable unsoldered LANs to reduce power consumption, but it still strongly recommend:  
 - Heatsink on Ralink Chip 

<img src="https://github.com/GorGylka/UDPBD-A5-V11/blob/main/heatsink.jpg" width=30% height=30%>
 
 - Hardmod MAX809TTR / ADM809 (Router doesn't always turn on after hard reboot, without it,)  

<img src="https://github.com/GorGylka/UDPBD-A5-V11/blob/main/max809ttr.jpg" width=30% height=30%>

-If you don't see the list of games, first try setting up UDPBD with configured USB on your PC  
-System does not have Plug-and-play feature. inject USB Drive before power on and eject after power off.  
-keepalive.txt file will be created on your flash drive. This is not a bug, but a feature-prevent USB HDD drives from parking.  


[img_photo]: https://github.com/GorGylka/UDPBD-A5-V11/blob/main/logo.jpg
