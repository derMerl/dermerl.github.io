---
title: 'Quickie: SVN umziehen'
author: derMerl
layout: post
permalink: /quickie-svn-umziehen/
categories:
  - IT
  - Quickie
tags:
  - Homeserver
  - svn
---
Es ist schön wenn einem Entwickler es so einfach machen.

1.  <pre>svnadmin dump /Pfad/zum/Repository &gt; reponame.dump</pre>

2.  <pre>svnadmin load /Pfad/zum/Repository &lt; reponame.dump</pre>

Und fertig ist der SVN Umzug. <img src="http://www.sysdump.de/wp-includes/images/smilies/icon_wink.gif" alt=";)" class="wp-smiley" />