---
tags:
  - ICTSAS432
  - Networking
  - Paul
  - howto
---
### What is a LAMP Server

LAMP Server is the common name of a type of web server, short for Linux Apache MySQL and PHP, a common stack of tools generally used for web content. 

## Setting up a LAMP Server

### Installing Linux (Ubuntu Server)

1. Using [Rufus](https://rufus.ie/en/), create a bootable Ubuntu Server USB. 
2. Key through the installer until you reach the network page. Set a static IP address.
3. Complete the installer, ensure you install SSH, and take note of the username and password of the machine.
4. After completion of the installer, remove the usb drive, and ensure the bios is set to UEFI mode. 
5. Using the static IP, username and password of the machine, SSH into the machine from a distance. 

Verify the machine is connected to the internet by running

``` 
ping 1.1.1.1
```

### Installing Apache

To install Apache on Ubuntu server, run the following commands;
```
sudo apt update
sudo apt install apache2
```

After installing Apache, start the service by running

```
sudo systemctl start apache2
```

Check the service started correctly with

```
sudo systemctl status apache2
```

Apache should now be installed. Navigate to your servers IP address in the browser, and you should find the Apache default landing page.

### Installing MySQL

To install MySQL on a Ubuntu Server, run the following commands
```
sudo apt update
sudo apt install mysql-server
```

Ensure the service is running with;
```
sudo systemctl status mysql
sudo systemctl start mysql
```

Next, configure MySQL to run on the servers IP address with the following command

```
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
```

Edit the following line to include your servers IP address.

```
bind-address            = 10.0.1.201
```

### Installing PHP

To install PHP on Ubuntu Server, run the following commands;

```
sudo apt update
sudo apt install php libapache2-mod-php
sudo systemctl restart apache2
```

PHP is now installed.

### Installing Wordpress

To install Wordpress on Ubuntu Server, run the following commands;

```
sudo mkdir -p /srv/www
sudo chown www-data: /srv/www
curl https://wordpress.org/latest.tar.gz | sudo -u www-data tar zx -C /srv/www
```

To configure Apache to serve Wordpress pages, create the following file
`/etc/apache2/sites-available/wordpress.conf`
```
<VirtualHost *:80>
    DocumentRoot /srv/www/wordpress
    <Directory /srv/www/wordpress>
        Options FollowSymLinks
        AllowOverride Limit Options FileInfo
        DirectoryIndex index.php
        Require all granted
    </Directory>
    <Directory /srv/www/wordpress/wp-content>
        Options FollowSymLinks
        Require all granted
    </Directory>
</VirtualHost>
```

Enable the site with

```
sudo a2ensite wordpress
```

Enable URL rewriting with:

```
sudo a2enmod rewrite
```

Disable the default landing page with:

```
sudo a2dissite 000-default
```

Finally, restart the service with:

```
sudo systemctl restart apache2
```