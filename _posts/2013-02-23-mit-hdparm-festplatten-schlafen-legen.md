---
title: Mit hdparm Festplatten schlafen legen
author: derMerl
layout: post
permalink: /mit-hdparm-festplatten-schlafen-legen/
categories:
  - IT
tags:
  - Hardware
  - Homeserver
  - Kauftipp
  - NAS
---
Ich habe gestern meinen Homeserver (<a href="http://www.amazon.de/MicroServer-TurionII-DualCore-1x4096MB-integrated/dp/B005LY5AXW/?_encoding=UTF8&camp=1638&creative=6742&linkCode=ur2&site-redirect=de&tag=d0borg-21" target="_blank">HP MicroServer N40L ca. 219€ @Amazon</a><img style="border: none !important; margin: 0px !important;" alt="" src="http://www.assoc-amazon.de/e/ir?t=d0borg-21&l=ur2&o=3" width="1" height="1" border="0" />) neu eingerichtet, auf dem guten Stück läuft nun wieder <a href="http://www.ubuntu.com/download/server" target="_blank">Ubuntu Server 12.04</a>.

In dem N40L habe ich 4x 2TB Samsung HDDs im Raid5 laufen, damit diese nicht den ganzen Tag laufen und Strom verbraten schalte ich sie nach 10 Minuten idle in Standby. Um das nicht jedes mal von Hand machen zu müssen habe mich mir den Befehl in die rc.local gepackt, hier ein kleines &#8220;howto&#8221;.

1.  **sudo vim /etc/rc.local**
2.  **hdparm -S 120 /dev/sda /dev/sdb /dev/sdc /dev/sdd** vor dem &#8220;exit 0&#8243; einfügen
3.  **reboot**

Einfach die Devices durch die bei euch passenden ersetzen und wenn gewünscht die Zeit anpassen.