#Networking #info #howto 

----

## What are IP addresses

## Subnet Mask

## IPv4 vs IPv6

## LAN Addressing

Local Area Networks, or LANs, use specific ranges of IP addresses. Generally one of these three ranges will be used.

**`10.0.0.0/8`** : One of the most common ranges to be used is this range. The available IPs range from `10.0.0.1` all the way to `10.255.255.254`, allowing for over 16 million connected devices. This is Scotts favorite range (he is deranged).

**`172.16.0.0/12`** : Easily the *least* common lan IP range, it spans from `172.16.0.0` up to `172.31.255.254`, allowing for a little of 1 million connected devices. 

**`192.168.0.0/16`** : The best LAN range, it spans from `192.168.0.0` up to `192.168.255.254`, allowing for 65 thousand connected devices. 

As a side note, only a portion of the 192 and 172 ranges are designated for LAN networks. In 2012, ARIN began allocating the 172 address space to internet service, wireless and content providers. There have been reports that some internet service providers have been denying devices having IPs from within the entire `172.0.0.0/8` range. 
Sited from [ARIN's official page](https://www.arin.net/reference/research/statistics/address_filters/) 

In a LAN, there will usually be a device managing the [DHCP service](DHCP.md), so IP addresses are handed out automatically on a lease. IP addresses can also be set on devices that require a static IP. 

### Setting a static IPv4 

Every device is different and requires a different process to set an IP. For this demonstration, we will use Windows Server 2022. 
1. In the Server Manager, navigate to `Local Server`
2. In the Properties panel, find `Ethernet0`, or if you have multiple Networks, the name of the network or NIC you want to set. Click the highlighted blue text. 
3. In the network connections window, select the network device you want to set a static IP for. 
4. Right click, and select `Properties`.
5. Select `Internet Protocol Version 4 (TCP/IPv4)`, and then go to properties 
6. Select the option `Use the following IP address`. At this stage you should know, or find, the IP configuration of your network.

Depending on your network configuration, the information you put into each box will be different. 


