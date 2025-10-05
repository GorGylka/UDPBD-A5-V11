![img_photo]
<h2 align="left">OpenWRT UDPBD for A5-V11 3G/4G Mini Router</h2>

<h3 align="left">Features:</h3>  

- Blazing 4.2mb/s speed   
- exFAT Support  
- external HDD, SSD, USB Drives up to 2TB  
- Lower power consumption by 45% ( No more overheating ( heatsink still recommended ) )


<img src="https://github.com/GorGylka/UDPBD-A5-V11/blob/main/compare.jpg" width=70% height=70%>
<h3 align="left">You will need:</h3>

- A5-V11 3G/4G (You must have 4MB Flash / 32MB RAM)  
- CH314A or other programmer  
- 8MB Flash W25Q64FV or similar  
- Any USB Drive

<h3 align="left">Router:</h3>

-Program the image (Releases) to 8mb flash  
-Swap memory chip on router  
-Router is Done!  

<img src="https://github.com/GorGylka/UDPBD-A5-V11/blob/main/flash_chip.jpg" width=50% height=50%>

<h3 align="left">USB Drive:</h3>

-Format USB to GUID Partition Table (GPT), exFat, Standart Cluster Size  
(I highly recommend using [GParted Live USB](https://gparted.org/liveusb.php) over Windows formatting)  
-Do standart USB config for PS2 (create CD/DVD folders, add backups, ARTs, e.t.c.)

<h3 align="left">PS2:</h3>

-Place OPNPS2LD-v1.2.0-Beta-1973-88079d7-UDPBD.elf into bootable memory card  
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

-I disable WiFi and disable unsoldered LANs to reduce power consumption, but it still strongly require heatsink on Ralink Chip and hardmod MAX809TTR / ADM809 is recommended 

<img src="https://github.com/GorGylka/UDPBD-A5-V11/blob/main/max809ttr.jpg" width=30% height=30%>

If you don't see the list of games, first try setting up UDPBD with configured USB on your PC  
I use 8 wire LAN cable. Cross 8 wire lan also works, but didnt test it on 4 wire / 4 cross wire  


[img_photo]: https://github.com/GorGylka/UDPBD-A5-V11/blob/main/logo.jpg
