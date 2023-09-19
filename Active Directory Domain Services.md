---
tags:
  - Networking
  - Scott
  - howto
  - vmware
  - info
---
## What is AD DS 

Active Directory Domain Services, or AD DS, is a directory service that allows administrators to manage and organize a network of computers and users in a Windows environment. It makes enforcing policies and security across a large environment significantly easier. 

#todo better explanation please

## Initial Installation & Set-up

As with any service on Windows server, it is installed by going to the `Add roles and features` menu. Active Directory Domain Services can be found the the `Roles` section. 

After installation, click the flag icon in the top right of the Server Manager window, and click the `Promote to Domain Controller` hyperlink. 

When asked to join or create a forest, select `Add a new forest`. This requires a root fully qualified domain name (cats.local)