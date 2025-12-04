# VM-setup

The projects goal is to understand how VMware workshop pro works and how to set up a VM using a windows installation. This is to get hand on experience with troubleshooting issues both with the software and a different installation process which was used to create the PC being used for this VM.

# Steps taken

* Download VMware Workstation pro free to use version for personal use through Broadcom from [VMware](https://support.broadcom.com/group/ecx/productfiles?subFamily=VMware%20Workstation%20Pro&displayGroup=VMware%20Workstation%20Pro%2025H2%20for%20Windows&release=25H2&os=&servicePk=&language=EN&freeDownloads=true)
* Download Proxmox ISO file from [proxmox](https://www.proxmox.com/en/downloads)
* Installation of VMware Workstation pro following prompts to complete
* Troubleshooting issue - See Ticket 1 for more information
* Create new machine in VMware Workstation pro using Proxmox as the base OS, following onscreen prompts and creating Log in for Proxmox Virtual Enviroment (PVE)
* Once installed select first option which opens Proxmox Shell
* Troublehsoot issue - See Ticket 2
* Type "ip a" to show IP configuration
* Troubleshooting issue - See Ticket 3 for further information
* Further use showing limitation for current goals as unable to utilize Proxmox for further VMs, see troubleshooting
* Delete VM with Proxmox OS
* Troubleshooting issue - See Ticket 4
* Download of windows 10 as a ISO file and create a new VM
* Troubleshooting issue - See Ticket 5
* Complete installation of windows 10 including windows log in
* Installation complete, VM working as intended and ready for future testing


# Troubleshooting

 ## Ticket 1 
 - Problem - VM give visual prompt that it is unable to start due to needing either VT-x enabled or AMD-V
 - Fix - Find sources online for issue, restart PC and enter BIOS by pressing DEL or F12, go to advance configuration, then advanced tab - CPU configuration - Intel Virtualization Technology - Enable
 - Cause - Setting is not always automatically turned on during PC set up and installation

## Ticket 2
- Problem - Installation of Proxmox not completing, stuck on instllation page with no further way to move forward or change settings within VM
- Fix - Delete VM with Proxmox OS, download Windows media creation tool, create installation for windows on USB, create new VM, on new installation machine window find Install from, click drop down menu and select OS, click next and proceed with installation
- Cause - Proxmox designed for higher specification PC, and as base OS for PC not VMs.

## Ticket 3
- Problem - No internet connection for device
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

 ## Ticket 4
 - Problem - OS not detected by software apon start up 
 - Fix - Fresh download of OS onto PC, create ISO file using windows media creation tool, create new VM and on new installation machine window find Installer disc image file (ISO):, click browse and find locatoin of saved ISO file, click on iso file the on open, brought back to the new installation machine window click next and follow on screen instructions for complete installation of new OS
 - Cause - USB drive corrupt with write protection turned on, unable to re-write onto usb or clear due to need of specialized software to clear protections and format

## Ticket 5
- Problem - EFI time out creating issues with installation on OS on each VM
- Fix - Ensure VM is turned off, right click on specific VM, go to settings, option tab, advanced, firmware type, select BIOS instead of UEFI, click ok
- Cause - Know issue with VMware Workshop pro due to incompatability with some motherboards
  



