---
tags:
  - ICTNWK420
  - VirtualMachine
  - Networking
  - Scott
  - howto
  - vmware
---
## The Network Properties
To see the Virtual Network properties, go to `Edit > Virtual Network Editor `. To change settings, add or remove networks, hit the `Change Settings` button in the bottom right, and allow access in the UAC prompt.

This is a very handy tool for creating new adapters, which creates separate LANs. 

### Add Network
To add a new network, press the `Add Network...` button. This will bring up a new prompt. Select the first available network, unless instructed otherwise. The new network will show up in the list of all usable networks. 

### Remove network
To remove a network, first select it in the list of available network. Make sure you select the right one, as **this action cannot be undone**. Once you have confirmed you have selected the correct network, press the `Remove Network...` button. There will not be a confirmation prompt.

### Rename network
Renaming networks will help with identifying the correct network when setting up a virtual machine. To rename a network, simply select the network in the list of all available networks, and press `Rename Network...`. This will bring up a prompt to rename the network. 

## VMnet Information

The VMnet information panel shows important information about the currently selected network. For info on the adapter type, see [Virtual Networking](Virtual%20Machines#Virtual%20Networking).

### Connect a host virtual adapter to this network
Generally, leave this option ticked. 
#todo find an explanation for this

### Use local DHCP
This option allows VMware workstation to act as a DHCP server for the network. For our use, we want this setting off. This will allow us to set up a DHCP server on our windows box, as having two DHCP servers can lead to issues. 

### Subnet IP and Subnet Mask
The subnet IP and subnet mask allow us to set a predefined range of IPs for the network. You will need to do this again during the Windows Server DHCP setup, however this can also act as a handy note for keeping track what ranges are already in use. 

Any range can be used as a local IP range, however generally one of three ranges will be used.

**`10.0.0.0/8`** : One of the most common ranges to be used is this range. The available IPs range from `10.0.0.1` all the way to `10.255.255.254`, allowing for over 16 million connected devices. This is Scotts favorite range (he is deranged).

**`172.16.0.0/12`** : Easily the *least* common lan IP range, it spans from `172.16.0.0` up to `172.31.255.254`, allowing for a little of 1 million connected devices. 

**`192.168.0.0/16`** : The best LAN range, it spans from `192.168.0.0` up to `192.168.255.254`, allowing for 65 thousand connected devices. 

As a side note, only a portion of the 192 and 172 ranges are designated for LAN networks. In 2012, ARIN began allocating the 172 address space to internet service, wireless and content providers. There have been reports that some internet service providers have been denying devices having IPs from within the entire `172.0.0.0/8` range. 
Sited from [ARIN's official page](https://www.arin.net/reference/research/statistics/address_filters/) 