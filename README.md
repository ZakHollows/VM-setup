# VM-setup

The purpose of this exercise is to set up a VM within the newly built pc running windows. This will be achieved by installing VMware Workstation player, installing Proxmox as the OS, followed by simulating an enviroment to set up a basic internet connection to a computer. This may be expanded apon within this project, or a new one created for more indepth exploration.

# Steps taken

* Download Proxmox ISO file from [proxmox](https://www.proxmox.com/en/downloads) 
* Download VMware Workstation pro free to use version through Broadcom from [VMware](https://support.broadcom.com/group/ecx/productfiles?subFamily=VMware%20Workstation%20Pro&displayGroup=VMware%20Workstation%20Pro%2025H2%20for%20Windows&release=25H2&os=&servicePk=&language=EN&freeDownloads=true)
* Run VM installing Graphical interface version of Proxmox, choosing Target Harddick location, country of origin.
* Create Admin log in
* Finish OS installation and rebbot VM
* 



# Troubleshooting

 ## Enabling VT-x 
 - Cause - VM would not start as this setting in the BIOS needed to be enabled.
 - Fix -  Restart and entered BIOS, setting with advance tab - CPU configuration - Intel Virtualization Technology - Enable

 ## OS not detected
 - Cause - VM not detecting OS and could not run
 - Fix - Delete previos OS download, download OS from official site. Open file to enable a bootable DVD disc in PC, set up new VM using new Boot up device, select Linux as OS version Debian 12.x 64-bit, set memory to 4GB and finish.


   Admin log in for Proxmox Hope_this_works_9876    email zak_hollows@outlook.com
