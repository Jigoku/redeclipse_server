redeclipse_server
=================

Slackbuild for redeclipse_server (svn)

This is the slackbuild script i use for deploying redeclipse svn
onto a Rasperry Pi.

Included are a cron script to keep the server online in the event
of a crash, and an rc script to manage the server.

Data files are stored in /etc/redeclipse
Eg; Place your maps into /etc/redeclipse/maps

<pre>
How to deploy:

 1.
 checkout svn version you need, into slackbuild directory, eg;
   $ svn co svn://svn.icculus.org/redeclipse -r 6967 .

 2.
 create the user redeclipse/nogroup(99)
   # /usr/sbin/useradd -u 220 -g 99 -d /etc/redeclipse -r redeclipse

 3. 
  # VERSION=r6967 ./redeclipse_server.Slackbuild

 4.
   # upgradepkg --reinstall /tmp/redeclipse_server-r6967-arm-1_uf.tgz

 5. (if required)
   # cp /etc/redeclipse/{servinit-example.cfg,servinit.cfg}

 6.
   # chmod +x /etc/rc.d/rc.redeclipse_server
   # /etc/rc.d/rc.redeclipse_server start
</pre>
