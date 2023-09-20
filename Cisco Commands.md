---
tags:
  - Networking
  - Scott
  - info
  - ICT40120
---
# Interfaces

**List Interfaces**

```
show ip int brief
```

**Select interface**

```
int [int-type][port-number]
```
* the 'int-type' can vary. list the interfaces, if the interface you want to select is 'FastEthernet', use "f". if the interface is 'GigabitEthernet', use "g"

**Set Trunkport (int)**

```
switchport trunk encapsulation dot1q
switchport mode trunk
switchport trunk allowed vlan [vlan id/s or all]
```

**Set Access Port (int)**

```
switchport mode access 
```

**Set Port VLAN**

```
switchport access vlan [vlan id]
```
# VLANs 

**List VLANs**

```
show vlan brief
```

**List Trunks and Allowed VLANS**

```
show int trunk
```

**Create VLAN (config)**

```
vlan [vlan id]
name [vlan name]
exit
```

**Delete VLAN (config)**

```
no vlan [vlan id]
```

**VLAN Routing (Layer 3 Switch)**

# VTP 

**Enable VTP (config)**

```
vtp mode [server/client]
```

**Set VTP Domain (config)**

```
vtp domain [domain name]
```
note: the VTP domain does *not* need to be a FQDN

**Set VTP Password (config)**

```
vtp password [password]
```

**Set VTP Version (VTP Server Only) (config)**

```
vtp version 2
```

**Show VTP Settings**

```
show vtp status
```

# Router Specific

**WAN IP Address (conf)**

```
int [wan link]
ip address [ip] 255.255.255.252
```
*We're using serial, your link should be s0/1/0*

**Enable Router RIP (conf)**

```
router rip
version 2
no auto-summary
```

**Enable EIGRP (config)**
```
router eigrp [asn]
no auto-summary
```

**Advertise Network (config-router)**

```
network [wan range]
network [lan range]
```
*works for rip and eigrp*

### Sub Interface

**Select Sub Interface (conf)**

```
int [interface].[subint num]
```

**Set Trunk Interface**

```
encapsulation dot1q [vlan num]
```

**Set Sub Interface IP**

```
ip address [IP Address] [Subnet]
```

**DHCP Forwarding**

```
ip helper-address [DHCP IP]
```

**Demo Sub Interface Setup**

```
int g0/0
no ip address
no shutdown
exit

int g0/0.1
encapsulation dot1q 1
ip address 10.0.0.1 255.255.255.0
no shutdown
```

# NAT

**Set WAN NAT**

```
int [wan int]
ip nat outside
```

**Set LAN NAT**

```
int [lan int]
ip nat inside
```
*outside must be set first*

**Create access control list**

```
access-list [ID] [Allow/Deny] [Network IP] [Inverse Subnet]
```

**Enable NAT on List**

```
ip nat inside source list [ID] interface [WAN int] overload 
```

