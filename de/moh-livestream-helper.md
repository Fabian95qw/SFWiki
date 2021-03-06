---
title: MOH Livestream Helper
description: 
published: true
date: 2021-04-07T13:50:33.645Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:35:21.892Z
---

# Beschreibung
Ein Gratistool welches auf der Starface MPG123 installiert, damit Livestreams als Warteschlangenmusik hinterlegt werden können.

**WARNUNG**
Das Tool kann nicht mehr entfernt werden, und es könnte zu komplikationen bei Updates kommen

**Gratislizenz: 2VSXC-TDY4K-7SHXG-4RF7W-F7NT7**
# Konfiguration
## Erstinstallation
Platzieren sie im MPG123 Download URL den Downloadlink zur MPG123 Version, die sie installieren wollen

Aktuelle URL's können unter: https://sourceforge.net/projects/mpg123/files/mpg123/ gefunden werden

Nach der platzierung des Downloadlinks muss das installationsscript ausgeführt werden, dies kann 5-10 Minuten dauern. Bitte überprüfen sie den **LOG** auf **DEBUG** Level auf den Fortschritt der Installation.

![1](/uploads/moh-livestream-helper/1.jpg "1")

## Streams Konfigurieren
In der Tabelle müssen jeweils Link der Warteschlangennamen, und rechts der dazugehörige Livestream der abgespielt werden soll platziert werden.

![2](/uploads/moh-livestream-helper/2.jpg "2")

## MPG123 Argumente
Hier können MPG 123 Argumente geändert werden, falls etwas mit den Streams nicht Ordnungsgemäss funktioniert.

Für Infos über die Argumente siehe: https://linux.die.net/man/1/mpg123

## Die Warteschlange bleibt still
Wenn eine Warteschlange leer bleibt heisst das, dass der Stream vermutlich nicht kompatibel ist.

Man kann dem Manuell nachgehen, indem man per SSH den Befehl: **/usr/local/bin/mpg123 -q -r 8000 -f 8192 -b 4096 --preload 0 --mono -s [URL zu MP3 stream]** eingibt.

Wenn nichts passiert, dann empfängt MPG123 nichts von diesem Stream. Wenn ein haufen Kauderwelsch zurückkommt, empfägt MPG123 Ordnungsgemäss die Daten.

## Die Warteschlange ist nach dem Neustart wieder auf der Standardmusik
Das Modul prüft in regelmässigen Abständen, ob die Music on Hold Config nocht richtig ist. 
Diese wird von der Starface überschrieben wenn:

* Die Anlage neu gestartet wurde
* Etwas im Music on Hold editiert wurde

Das heisst, je nach Timing hat das Modul die Konfiguration noch nicht wieder überschrieben, und es wird die Standardmusik abgespielt.
# Manuelles Installationsscript
Sollte aus irgendeinem grund das automatische Script nicht funktionieren, kann dies per SSH manuell durchgeführt werden.

`mv /etc/yum.repos.d/starface.repo /etc/yum.repos.d/starface.repo.copy //Starface Repository Sichern`
`cp /var/starface/module/modules/repo/75ad75a3-a423-4c45-b442-9930d2cd7702/res/0efc550c-6bd8-405a-b606-b2a2f070734a.repo /etc/yum.repos.d/starface.repo //Neues Repository platzieren`
`yum clean all //Yum Cleanup, damit die Repository Daten refresht werden`
`yum -y groupinstall "Development Tools" //Development Tools herunterladen`
`cd /usr/src //Verzeichnis Wechseln`
`wget [MPG123 URL] //MPG123.tar.gz herunterladen`
`tar -xjvf  mpg123* //tar.gz entpacken`
`cd /usr/src/mpg123*/ && ./configure;cd /usr/src/mpg123*/ && make;cd /usr/src/mpg123*/ && make install //In das Verzeichnis wechseln, die MPG123 Quelle konfigurieren, kompillieren, und anschliessend installieren`
`make clean //Make bereinigen`
`cd /usr/src && rm -r -f mpg123*; //Source verzeichnis entfernen`
`rm -f /etc/yum.repos.d/starface.repo //Repository wieder löschen`
`mv /etc/yum.repos.d/starface.repo.copy /etc/yum.repos.d/starface.repo //Original Starface Repository wieder platzieren`

# Manuelles Aufzwingen von Livestreams ohne Modul
* Die Datei: /etc/asterisk/musiconhold.conf editieren
* Die Warteschlange raussuchen

Die warteschlange Anpassen auf:

[Warteschlangenname]
mode=**custom**
Directory: **nodir**
application=**/usr/local/bin/mpg123 -q -r 8000 -f 8192 -b 4096 --preload 0 --mono -s [URL zu MP3 stream]**
Format=**slin**

* Nach Angepasster Warteschlange in der Asterisk Console (**asterisk -rv** im Terminal) den Befehl "**moh reload**" ausführen.
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch/de/lizenzierung
