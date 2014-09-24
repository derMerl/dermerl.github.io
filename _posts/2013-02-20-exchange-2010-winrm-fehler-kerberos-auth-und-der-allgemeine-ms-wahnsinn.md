---
title: 'Exchange 2010: WinRM Fehler, Kerberos Auth und der allgemeine MS Wahnsinn'
author: derMerl
layout: post
permalink: /exchange-2010-winrm-fehler-kerberos-auth-und-der-allgemeine-ms-wahnsinn/
categories:
  - IT
tags:
  - Exchange
  - Microsoft
---
Gestern war ein schlechter Tag. Oh ja!

Gegen Mittag stellte ich fest das es mir nicht mehr möglich war auf die Exchange Management Console unseres Mailservers zu kommen, auch die Exchange Management Shell verweigerte den Dienst.

Als Fehlermeldung bekam ich einen Fehler 500 sowie den Hinweis auf eine nicht funktionierende Kerberos Authentifizierung, die Ereignisanzeige gab es nur zwei &#8220;aussagekräftige&#8221; Fehler aus.

> *   Der Microsoft Exchange Active Directory-Topologiedienst auf dem Server localhost ist nicht über RPC erreichbar.
> *   Fehler bei RPC-Anforderung an den Microsoft Exchange Active Directory-Topologiedienst

Nach einiger Recherche stieß ich immer wieder auf den sogenannten WinRM Fehler, welcher in einem Blogpost im Technet unter dem Namen &#8220;<a href="http://blogs.technet.com/b/exchange/archive/2010/02/04/3409289.aspx" target="_blank">Troubleshooting Exchange 2010 Management Tools startup issues</a>&#8221; beschrieben und zu dem dort auch diverse Lösungsansätze vorgeschlagen waren. Leider schaffte keiner davon Abhilfe, bzw. unser Exchange Server war wie beschrieben konfiguriert. Jedoch wusste ich nun woran es wohl zu liegen hat.

> To start off, you first need to be aware that in Exchange 2010, all management is done via Remote PowerShell, even when opening the Management Tools on an Exchange server. Where this differs from Exchange 2007 is that there is now a much larger dependency on IIS, as Remote PowerShell requests are sent via the HTTP protocol and use IIS as the mechanism for connections. IIS works with the WinRM (Windows Remote Management) service, and the WSMan (Web Services for Management) protocol to initiate the connection.

Alle IIS Einstellungen schienen korrekt zu sein, jedoch entwickelte ich ein Störgefühl bei dem &#8220;Virtual Directory PowerShell&#8221; im IIS. Drei Tassen Kaffe später hatte ich des Rätzels Lösung gefunden und mein Verdacht bestätigte sich. Ein Artikel auf <a href="http://www.administrator.de" target="_blank">administrator.de</a> mit der treffenden Bezeichnung &#8220;<a href="http://www.administrator.de/wissen/exchange-2010-und-die-winrm-fehler-145070.html" target="_blank">Exchange 2010 und die WinRM-Fehler</a>&#8221; beschrieb detailliert meinen &#8220;Leidensweg&#8221; und offenbarte schließlich die Lösung.

1.  <span style="line-height: 13px;">Benötigte Cmdlets via PowerShell verfügbar machen</span>
2.  AuthenticationMethod des VD PowerShell als Ursache identifizieren
3.  Fehlerhaftes VD PowerShell entfernen
4.  VD PowerShell neu anlegen
5.  ggf. SSL Zwang deaktivieren

Danach funktionierte nun endlich wieder alles so wie es sollte. Weitere Informationen sind in den verlinkten Artikeln zu finden.