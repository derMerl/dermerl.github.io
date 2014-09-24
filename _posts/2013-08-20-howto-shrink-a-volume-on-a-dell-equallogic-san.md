---
title: 'HOWTO: Shrink a volume on a DELL EqualLogic SAN'
author: derMerl
layout: post
permalink: /howto-shrink-a-volume-on-a-dell-equallogic-san/
categories:
  - IT
tags:
  - CLI
  - DELL
  - EqualLogic
  - SAN
  - shrink
---
Hier ein kurzes HOWTO für alle die mal in die Situation kommen ein Volume auf einer <a href="http://www.dellstorage.com/equallogic/" target="_blank">Dell EqualLogic SAN</a> verkleinern zu müssen. Zuerst solltet ihr natürlich über ein valides Backup verfügen denn trotz aller Vorsicht kann es bei einer solchen Aktion zu Datenverlust kommen. Zusätzlich sollte dem Volume 10% Snapshot Space zugewiesen sein, denn bei dem verkleinern wird automatisch ein Snapshot angelegt. Die <a href="https://de.wikipedia.org/wiki/SAN" target="_blank">SAN</a> sollte Firmware V3.2.x oder höher bzw. wenn es um ein  &#8220;<a href="https://de.wikipedia.org/wiki/Thin_Provisioning" target="_blank">Thin Provisioned Volume</a>&#8221; geht Version 4 oder höher haben. Nun aber zum eigentlichen &#8220;shrink&#8221; Vorgang.

Dieser kann nur über das Command Line Interface eingeleitet werden, dazu müsst ihr via SSH Client (z.B. <a href="http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html" target="_blank">Putty</a>) auf eure EqualLogic. Die Syntax zum verkleinern ist folgende:

> GrpName> vol sel <volume name>
> 
> GrpName(volume\_volume\_name)> offline
> 
> GrpName(volume\_volume\_name)> shrink <new capacity>
> 
> GrpName(volume\_volume\_name)> online
> 
> &nbsp;

Und hier anhand eines Beispiels mit der Group &#8220;EQLSAN\_A&#8221; und dem Volume &#8220;vmware\_01&#8243;:

> EQLSAN\_A> volume select vmware\_01
> 
> EQLSAN\_A(volume\_vmware_01)> offline
> 
> EQLSAN\_A(volume\_vmware_01)> shrink ?
> 
> <new-size> &#8211; New size of the volume in MB (default) or GB.
> 
> For example: 100MB. (1GB=1024MB; 1MB=1024KB; 1KB=1024B)
> 
> EQLSAN\_A(volume\_vmware_01)> shrink 650GB
> 
> EQLSAN\_A(volume\_vmware_01)> online
> 
> EQLSAN\_A(volume\_vmware_01)> exit

Es ist unbedingt darauf zu achten ein Volume nicht kleiner als das darauf befindliche Dateisystem zu machen, denn das würde zu Datenverlust führen. Also vorher ggf. das Dateisystem verkleinern. Wenn Ihr euer Dateisystem also auf 100Gb verkleinert habt, sorgt dafür das euer Volume mindestens 101GB groß ist.

Mehr Informationen gibt es <a href="http://en.community.dell.com/support-forums/storage/f/3775/p/19492184/20310205.aspx#20310205" target="_blank">im Dell EqualLogic Support Forum</a>, aus welchem auch meine stammen.