#Networking #Scott #howto 

----

### Change to a private network profile

By default, the [[Windows Server]] firewall profile is set for Public Networks. For our use case this isn't ideal. We'll change it to private. Please note; PowerShell supports tab-completion.

1. Open PowerShell as Administrator
2. Run `get-netconnectionprofile`
This will return properties about the current connection profile. Take note of the `InterfaceIndex`

3. Run `set-netconnectionprofile -InterfaceIndex <enter your interface index number here> -NetworkCategory private`

### Allowing Pings

By default, Windows Server also blocks the ICMP protocol (Pings). This is a terrible idea, if you want to disable this protocol, please read [this](http://shouldiblockicmp.com/). To allow pings on Windows Server;

1. Open `Windows Defender Firewall with Advanced Security`
2. Right click Inbound Rules on the left side panel, then select `New Rule...`
3. Select `Custom` for rule type.
4. Allow all programs.
5. In the `Protocol Type` dropdown menu, select `ICMPv4`
6. Hit next, until you get to the last window to name the new rule. Call it `Allow ICMPv4`

Repeat those steps for an Outbound rule. 

You will now be able to ping the server. Ideally, ICMPv6 should also be allowed through, however, it's only really beneficial if you plan on using IPv6 in your network. 