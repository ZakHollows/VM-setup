# VM-setup

The goal of this is to have a functioning workspace to practice VMs in the future, and will be a walkthrough of how to install and troubleshoot the software used to create VM's

# Steps taken

* Download VMware Workstation pro free to use version for personal use through Broadcom from [VMware](https://support.broadcom.com/group/ecx/productfiles?subFamily=VMware%20Workstation%20Pro&displayGroup=VMware%20Workstation%20Pro%2025H2%20for%20Windows&release=25H2&os=&servicePk=&language=EN&freeDownloads=true)
* Download Proxmox ISO file from [proxmox](https://www.proxmox.com/en/downloads)
* Installation of VMware Workstation pro following prompts to complete
* Create new machine in VMware Workstation pro using Proxmox as the base OS, following onscreen prompts and creating Log in for Proxmox Virtual Enviroment (PVE)
* Select amount of resources avaiable to VM from PC
  - CPU Type: Select Host
  - Sockets: 1
  - Cores: 4
  - Memory: 2GB
  - Storage: SSD
  - Networking: Bridged
  - Disk Bus: VirtIO
  - Disk Alignment: Improve SSD performance
* Once installed select first option which opens Proxmox Shell
* Type "ip a" to show IP configuration
* Troubleshooting needed to establish internet connection, see below for steps taken
* Further use showing limitation for current goals as unable to utilize Proxmox for further VMs, see troubleshooting
* Delete VM with Proxmox OS

new issue of trying to set up a new vm, usb is corrupted and write protected so unable to format. have used run command window and typed "diskpart" command which take away the read only files. after run command entered command window opens, type "list disk", the type "select disk 1" (disk that is the same storage size as the usb), type "attributes disk", see if read only is yes or no, type "attributes disk clear readonly" is read only is yes.
Issue persists
Download of application Rufus to wipe the usb of any corrupt files and write protections



# Troubleshooting

 ## Enabling VT-x 
 - Cause - VM would not start as this setting in the BIOS needed to be enabled.
 - Fix -  Restart and entered BIOS, setting with advance tab - CPU configuration - Intel Virtualization Technology - Enable

 ## OS not detected
 - Cause - VM not detecting OS and could not run
 - Fix - Delete previos OS download, download OS from official site. Open file to enable a bootable DVD disc in PC, set up new VM using new Boot up device, select Linux as OS version Debian 12.x 64-bit, set memory to 4GB and finish.

## No internet connection in VM
# troubleshooting steps
- Restart VM and check internet connection again using "ip a" in VM
- Vmware Workstation settings for internet connection using bridges connection, check "ip a" for connection
- IP address showing, attempt to connect through browser on PC using IP address to connect to PVE portal
- Couldn't reach server
- In VM in Proxmox shell type "ping" followed by IP address shown in "ip a"
- 4 packets sent, 0 packets recieved, 4 packets lost
- Vmware Workstation settings for internet connection changed from bridged to NAT
- VM shut down, application closed
- VMware opened, Start VM and type in shell "ip a"
- IP address showing, use "ping (IP adress)
- 4 packets sent, 4 packets recieved, 0 packets lost
- On PC browser type in IP address to access PVE and log in
- Portal now accessed
- 
## Proxmox incorrect OS
- Cause - Further investigation show this OS Proxmox is meant for installing on the base PC which the VMs wil be run on, not the VMs themselves
- Fix - Delete created VM with Proxmox OS, download Windows media creation tool, create bootable device using USB drive, create new VM using the windows OS on the USB


   Admin log in for Proxmox Hope_this_works_9876    email zak_hollows@outlook.com
