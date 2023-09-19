<sub>(A lot of info has been pulled from the Wazuh docs, while most of the how-to crap was written by me)</sub>

Wazuh is a free and open source security platform that unifies XDR (Extended Detection Response) and SIEM (Security Information and Event Management) capabilities. It protects workloads across on-prem, virtualized, containerized, and cloud-based environments. 

TLDR; Wazuh is a security monitoring and management platform that is free, open source and extremely reliable. 

## Installing Wazuh

We're going to use the "Quick start" automated way of installing Wazuh, as it provides all the components onto the same machine in just a few minutes. 

### Requirements

The hardware requirements of Wazuh are fairly small, although not insignificant, especially if you're running this in a virtualized environment. 

| Clients | CPU | RAM | Storage (90 Days) |
| --- | --- | --- | --- |
| 1-25 | 4 vCPU | 8GB | 50GB |
| 25-50 | 8vCPU | 8GB | 100GB |
| 50-100 | 8vCPU | 8GB | 200GB |

Wazuh can be installed on any 64-bit Linux operating system. We'll be using Ubuntu Server 22.04.

### Install process

1. Download and run Wazuh installer assistant
```
curl -sO https://packages.wazuh.com/4.5/wazuh-install.sh && sudo bash ./wazuh-install.sh -a
```

After the installer finishes, it should spit out something like the following.
```
INFO: --- Summary ---
INFO: You can access the web interface https://<machine-ip>
    User: admin
    Password: <ADMIN_PASSWORD>
INFO: Installation finished.
```

Head to the web interface listed by the output to finish up. 

### Forgot my password

The password for Wazuh is randomly generated and outputted once, at the end of installation. If you're like me and didn't change it straight away, you'll probably forget it. Here's how you can get the password without doing a total reinstall. 

1. SSH into the machine Wazuh is installed on. (or use a baremetal connection like a keyboard and monitor if you swing that way).
2. Find where  you installed Wazuh. This will probably be in the home directory.
3. Run the following command
```
sudo tar -xvf wazuh-install-files.tar
```
4. cd into the newly created folder, and `cat` the `wazuh-passwords.txt` file

## Wazuh Monitoring

