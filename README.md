#redeclipse_server
=================
Slackbuild script for redeclipse_server

This is the slackbuild script i use for deploying a redeclipse server onto a Rasperry Pi box running slackware linux.

Included are a cron script to keep the server online in the event of a crash, and an /etc/rc.d/ script to manage the server.

Data files are stored in /etc/redeclipse
Eg; Place your maps into /etc/redeclipse/maps

## How to deploy

1. Clone the git branch you want, into the slackbuild directory, eg;
##### Stable
```git clone -b stable https://github.com/red-eclipse/base.git base```
##### Development
```git clone https://github.com/red-eclipse/base.git base```
   
2. create the user redeclipse/nogroup(99)
```# /usr/sbin/useradd -u 220 -g 99 -d /etc/redeclipse -r redeclipse```
 
3. run the slackbuild
```# VERSION=dev ./redeclipse_server.Slackbuild```
 
4. install the package
```# upgradepkg --reinstall /tmp/redeclipse_server-stable-arm-1_uf.tgz```

5. create servinit.cfg (if required)
```# cp /etc/redeclipse/{servinit-example.cfg,servinit.cfg}```

6. enable the service
```# chmod +x /etc/rc.d/rc.redeclipse_server```

## Managing the server  
Start the server
```# /etc/rc.d/rc.redeclipse_server start```

Stop the server
```# /etc/rc.d/rc.redeclipse_server stop```

Check the status of the server
```# /etc/rc.d/rc.redeclipse_server check```
