# Additional Ethernet Adapters VMware vSphere 6.7
This is complete guide to install TP-Link USB 3.0 to Ethernet Gigabit Adapter(UE300) on VMware vSphere v6.7

## Getting Started
There is some step we need to be done before install the **TP-Link UE300**, here are what needs to be done :
1. **Buy a TP-Link UE300**
1. **Connect TP-Link UE300 to VMware vSphere Server**
1. **Download TP-Link UE300 Driver**
1. **Enable vSphere SSH Service**
1. **Install TP-Link UE300 Driver on VMware vSphere Server**

## Buy a TP-Link UE300
First thing we need to to do, of course buy the TP-Link device which will be used for vSphere server additional adapter. The full name of the product is [TP-Link USB 3.0 to Gigabit Ethernet Network Adapter UE300](https://www.tp-link.com/id/home-networking/computer-accessory/ue300/), which any of you can find in any local computer store near your place or maybe in one of the online store. And it just need around $14 from your pocket.

For image of the device, you can inspect file **tp-link-ue300.jpg** in this repository.

## Connect TP-Link UE300 to VMware vSphere Server
Second step, connect your TP-Link device to your vSphere server via USB port. Then connect your TP-Link device with switch device using the ethernet cable, and make sure your ethernet cable works fine.

## Download TP-Link UE300 Driver
Third step, download the driver. TP-Link UE300 cannot detect by vSphere without the driver.

The driver itself can be downloaded from this repository. The name of the driver is **r8152-2.06.0-4_esxi65.vib**

## Enable vSphere SSH Service
Fourth step, enabling SSH service on your vSphere server.

**Questions** : Why the hell we need SSH to install the driver?

**Answer** : Because the installation of a driver cannot be done in vSphere Client, it must be done with CLI. That is what cause us to enable the SSH service.

Here are the steps to enable SSH service on vSphere server :

* Access directly to vSphere Client or vSphere Web Client from web browser
* Login with root credentials & its password
* Select **Manage** menu
* Select **Services** menu, the position of Services menu is number 2 from the right.
* Start **SSH** & **ESXI Shell** service.
* Test SSH from your local computer to the vSphere server with putty or directly from terminal.
```
ssh root@(vsphere-ipaddress)
```
* Done.

## Install TP-Link UE300 Driver on VMware vSphere Server
Last step, install the driver. Here are the steps to do that properly :

* Transfer the driver file (**r8152-2.06.0-4_esxi65.vib**) to the vSphere server with WinSCP or directly SCP command fromt terminal. 

**Note** : Transfer the driver file to **/var/log/vmware/** directory.
```
scp r8152-2.06.0-4_esxi65.vib root@(vsphere-ipaddress):/var/log/vmware/
```
* SSH from your local computer to the vSphere server with putty or directly from terminal
```
ssh root@(vsphere-ipaddress)
```
* Install the driver with these command below
```
esxcli software vib install -v r8152-2.06.0-4_esxi65.vib -f

esxcli system module set -m = vmkusb -e = FALSE
```
* Reboot your vSphere server.
```
reboot
```
* Check your vSphere server from vSphere client or vSphere web client.
* Select **Networking** menu.
* Select **Physical NICs**, the position of that menu is number 3 from the left.
* Make sure there is an addtional adapter in the menu.
* Done.
