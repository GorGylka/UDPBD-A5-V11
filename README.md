# UDPBD-A5-V11
OpenWRT UDPBD for A5-V11 3G/4G Mini Router

To run the UDPBD on the 3g/4g A5-v11 Router
You will need:
-CH314A programmer
-8MB Flash W25Q64FV or similar
-Any USB Drive
A5-V11 Router:
Program the image (below) to 8mb flash
swap memory chip on router
Router is Done!
USB Drive:
Format USB to GUID partition table / GPT, exFat, Standart Cluster Size
I highly recommend using GParted Live USB over Windows formatting
Do standart USB config for PS2 (create CD/DVD folders, add backups, ARTs, e.t.c.)
PS2:
place OPNPS2LD-v1.2.0-Beta-1973-88079d7-UDPBD.elf into bootable memory card
delete/archive opl .cfg files, there are stored in:
mc0:/OPL/conf_network.cfg
mc0:/OPL/conf_opl.cfg
make this version of OPL apperable on FMCB/Funtuna menu or config to autoboot this version of OPL
remove any USB Drive from PS2 (important!)
Connect power to the router, having first connected the LAN to PS2 and USB Drive to router
run OPNPS2LD..UDPBD
Settings->BDM Start Mode->Manual
Settings->Default Menu->BDM Games->OK->Save Changes
Notes:
Router take some time to start and init. I didn't time it exactly, please wait 2 minutes in FMCB Menu or press Start ->Exit -> (run OPL
I disable WiFi and disable unsoldered LANs to reduce power consumption, but it still strongly require heatsink on Ralink Chip and hardmod MAX809TTR / ADM809 is recommended (see some posts above)
If you don't see the list of games, first try setting up UDPBD with configured USB on your PC
I use 8 wire LAN cable. Cross 8 wire lan also works, but didnt test it on 4 wire / 4 cross wire
