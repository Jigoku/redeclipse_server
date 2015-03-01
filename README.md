#redeclipse_server

Creates a slackware package for redeclipse (standalone server).

## What does it do?
This is the slackbuild script i use for deploying a redeclipse server onto a Rasperry Pi box running slackware linux.

Included are a cron script to keep the server online in the event of a crash, automatically restarting the server within 1 minute, and an /etc/rc.d/ script to start or stop the service.

- Place your server maps in /etc/redeclipse/maps
- servinit.cfg should be at /etc/redeclipse/servinit.cfg

## How to deploy
1. Clone the git branch you want, into the slackbuild directory, eg;
    * Stable
    
        ```git clone -b stable https://github.com/red-eclipse/base.git base```
    * Development
    
        ```git clone https://github.com/red-eclipse/base.git base```
2. Create the user 'redeclipse/nogroup(99)'

    ```# /usr/sbin/useradd -u 220 -g 99 -d /etc/redeclipse -r redeclipse```
3. Run the slackbuild

    ```# VERSION=git ./redeclipse_server.Slackbuild```
4. Install the package

    ```# upgradepkg --reinstall --install-new /tmp/redeclipse_server-git-arm-1_uf.tgz```
5. Create a servinit.cfg (if required)

    ```# cp /etc/redeclipse/{servinit-example.cfg,servinit.cfg}```
6. Enable the service

    ```# chmod +x /etc/rc.d/rc.redeclipse_server```

## Managing the server  
Start the server
```# /etc/rc.d/rc.redeclipse_server start```

Stop the server
```# /etc/rc.d/rc.redeclipse_server stop```

Restart the server
```# /etc/rc.d/rc.redeclipse_server restart```

Check if the server needs to be restarted
```# /etc/rc.d/rc.redeclipse_server check```


### Why does the server keep restarting, even though i 'stopped' it? 
You need to run
```
chmod -x /etc/rc.d/rc.redeclipse_server
```
otherwise cron will think it needs to be restarted.
