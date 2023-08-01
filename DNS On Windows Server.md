#Networking #Scott #howto #vmware 

---

## How to set up and use DNS on windows server

To use [[windows server]] as a DNS server, the machine **must** have a [static IPv4 address](IP%20Addressing#Setting%20a%20static%20IPv4). 

1. Add the DNS role to the server, head to `Manage` > `Add roles and Features`
Please note, if you have already installed [[Active Directory Domain Services]], DNS will already be installed.

2. In `Server Roles`, make sure `DNS Server` is ticked. Click `Add Features` in the dialogue that pops up
3. Hit next until you can click install, then click install. 

The DNS service will show up in the left side panel of the server manager. To set up and edit our DNS server, we need to open the DNS manager window, from the Windows start menu (Windows key).

### Setting up the Forward zone

A forward zone will resolve a domain name (ie. yourname.local) to the relevant IP address. 

1. In the DNS Manager window, click on the Windows Server name, then click `Action` > `New Zone...` on the top bar. 
2. Hit `Next` and then `Primary Zone`
3. Select `Forward Zone` and `Next`
4. The zone name will be the root of the domain that this DNS will be authoritative for, or more simply, the domain it will manage, for example, yourname.local
5. Select `Create a new file with this file name`. Leave the name as the default name and select `Next`
6. Select `Do not allow dynamic updates` and `Next`
7. Confirm the settings are correct and hit `Finish`

If you were to send a request to this server for youtube.com it won't be able to answer it. This is where a forwarder is handy, for pointing to another DNS server that can answer everything.

1. Right click the name of the DNS server in the DNS Manager and go to `Properties`
2. Inside properties, click `Forwarders`
3. Select `Edit`. This will bring up the dialogue for adding DNS servers. If you have a preferred DNS server, put it here, otherwise, use Cloudflare by entering `1.1.1.1`

### Creating DNS records
