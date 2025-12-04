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
During this process as it takes some time download of windows 10 os iso file onto pc to use as the OS for a new vm



# Troubleshooting

 ## Enabling VT-x 
 - Problem - VM give visual prompt that it is unable to start due to needing either VT-x enabled or AMD-V
 - Fix - Find sources online for issue, restart PC and enter BIOS by pressing DEL or F12, go to advance configuration, then advanced tab - CPU configuration - Intel Virtualization Technology - Enable
 - Cause - Setting is not always automatically turned on during PC set up and installation

- ## Proxmox incorrect OS
- Problem - Installation of Proxmox not completing, stuck on instllation page with no further way to move forward or change settings within VM
- Fix - Delete VM with Proxmox OS, download Windows media creation tool, create installation for windows on USB, create new VM, on new installation machine window find Install from, click drop down menu and select OS, click next and proceed with installation
- Cause - Proxmox designed for higher specification PC, and as base OS for PC not VMs.

 ## OS not detected
 - Problem - OS not detected by software apon start up 
 - Fix - Fresh download of OS onto PC, create ISO file using windows media creation tool, create new VM and on new installation machine window find Installer disc image file (ISO):, click browse and find locatoin of saved ISO file, click on iso file the on open, brought back to the new installation machine window click next and follow on screen instructions for complete installation of new OS
 - Cause - USB drive corrupt with write protection turned on, unable to re-write onto usb or clear due to need of specialized software to clear protections and format

## No internet connection in VM
- Problem - No internet connection showing
- Troubleshooting steps and fix:
* Restart VM and check internet connection again using "ip a" in VM
* Vmware Workstation settings for internet connection using bridges connection, check "ip a" for connection
* IP address showing, attempt to connect through browser on PC using IP address to connect to PVE portal
* Couldn't reach server
* In VM in Proxmox shell type "ping" followed by IP address shown in "ip a"
* 4 packets sent, 0 packets recieved, 4 packets lost
* Vmware Workstation settings for internet connection changed from bridged to NAT
* VM shut down, application closed
* VMware opened, Start VM and type in shell "ip a"
* IP address showing, use "ping (IP adress)
* 4 packets sent, 4 packets recieved, 0 packets lost
* On PC browser type in IP address to access PVE and log in
* Portal now accessed
- Cause - Incompatability issue with motherboard using bridge connection for internet access

## EFI time out
- Problem - EFI time out creating issues with installation on OS on each VM
- Fix - Ensure VM is turned off, right click on specific VM, go to settings, option tab, advanced, firmware type, select BIOS instead of UEFI, click ok
- Cause - Know issue with VMware Workshop pro due to incompatability with some motherboards
  



