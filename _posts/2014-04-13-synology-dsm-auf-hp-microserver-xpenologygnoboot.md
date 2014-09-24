---
title: Synology DSM auf HP Microserver (XPEnology/gnoBoot)
author: derMerl
layout: post
permalink: /synology-dsm-auf-hp-microserver-xpenologygnoboot/
categories:
  - IT
tags:
  - Hardware
  - Homeserver
  - NAS
---
Ich benutze seit einiger Zeit <a href="http://xpenology.com/forum/" target="_blank">XPEnology </a>auf meinem <a href="http://www.amazon.de/gp/product/B00AKWUUXU/ref=as_li_ss_tl?ie=UTF8&camp=1638&creative=19454&creativeASIN=B00AKWUUXU&linkCode=as2&tag=d0borg-21" target="_blank">HP Microserver N40L</a><img style="border: none !important; margin: 0px !important;" alt="" src="http://ir-de.amazon-adsystem.com/e/ir?t=d0borg-21&l=as2&o=3&a=B00AKWUUXU" width="1" height="1" border="0" /> und bin damit sehr zufrieden. In meinem [&#8220;Ping&#8221;][1] Post habe ich angekündigt eine kurz Anleitung darüber zu schreiben, auf <a href="http://d3dx9.de" target="_blank">d3dx9.de</a> ist mir da allerdings jemand zuvor gekommen und das so gut das ich dies hier einfach einmal verlinken möchte.

*   Erstinstallation: <a href="http://d3dx9.de/post/4" target="_blank">N54L und Synology, aber wie?</a>
*   Wie man Updates einspielt: <a href="http://d3dx9.de/post/5" target="_blank">gnoBoot: Update auf 4458 Update 1</a>
*   Upgrade von Trantor auf gnoBoot: <a href="http://d3dx9.de/post/6" target="_blank">Upgrade von DSM4.3/DSM5 Beta von Trantor auf DSM 5 4458 &#8211; gnoBoot</a>

Die dort beschriebenen Methoden basieren nicht mehr auf dem Builds von <a href="http://xpenology.com/forum/viewtopic.php?f=14&t=1700" target="_blank">Trantor</a>, sondern nutzen &#8220;gnoBoot&#8221; um DSM zu booten. Das hat entscheidende Vorteile z.B.:

*   No need to edit vender files, uses real mac address
*   Silent and cleaner boot up messages with colorized console
*   Works with original or custom version 4.x/5.x pat files, tested with DS3612xs & RS3614xs+ pat files.
*   VMware fully supported
*   Modular drivers
*   Synoboot block device
*   Custom boot options &#8211; insmod/rmmod=driver\_name, gnoboot\_upgrade

Bei Fragen einfach in die Kommentare schreiben ich helfe dann gerne.

 [1]: http://www.sysdump.de/ping/