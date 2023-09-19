---
tags:
  - Networking
  - howto
  - Scott
---
## DHCP

DHCP, or "Dynamic Host Configuration Protocol" (which you will probably never say again), is an extremely common network protocol that automatically assigns IP addresses and other network configuration settings to devices on a network. 

## Setting up DHCP (on windows server)

First step of setting up DHCP, as with everything on Windows Server, is installing the role. After installing the role, head to the "Notifications" panel in Server Manager (the flag icon), and click `Complete DHCP Configuration`. In the window that pops up, hit `Commit` and `Finish`. 
DHCP won't start working on it's own, it needs a scope of settings to hand out. To create a scope;

1. Open the DHCP app
2. Under your server name, click `IPv4`
3. Go to `Action > New Scope`
4. Enter a name for the scope, i.e "Default"
5. Enter the start and end of the range of IP addresses you want to assign. For example, `Start: 192.168.50.100 End: 192.168.50.200`. This will automatically assign IPs between those two bounds. 
6. The subnet mask will autofill, however, you can change it to fit your needs.
7. Add any required exclusions in the next window. 