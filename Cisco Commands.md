#Networking #Scott #info #ICT40120 

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


# VTP 

**Enable VTP**

```
vtp mode [server/client]
```

**Set VTP Domain**

```
vtp domain [domain name]
```
note: the VTP domain does *not* need to be a FQDN

**Set VTP Password**

```
vtp password [password]
```

**Set VTP Version (VTP Server Only)**

```
vtp version 2
```

