---
title: MOH Livestream Helper
description: 
published: true
date: 2023-03-21T14:58:03.499Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:35:21.892Z
---

# Beschreibung
Ein Gratistool welches auf der Starface MPG123 installiert, damit Livestreams als Warteschlangenmusik hinterlegt werden können.

> Das Tool kann nicht mehr entfernt werden, und es könnte zu komplikationen bei Updates kommen
{.is-warning}


# Konfiguration
## Erstinstallation
Platzieren sie im MPG123 Download URL den Downloadlink zur MPG123 Version, die sie installieren wollen

Aktuelle URL's können unter: https://sourceforge.net/projects/mpg123/files/mpg123/ gefunden werden

Nach der platzierung des Downloadlinks muss das installationsscript ausgeführt werden, dies kann 5-10 Minuten dauern. Bitte überprüfen sie den **LOG** auf **DEBUG** Level auf den Fortschritt der Installation.

![1](/uploads/moh-livestream-helper/1.jpg "1")

## Streams Konfigurieren
In der Tabelle müssen jeweils Link der Warteschlangennamen, und rechts der dazugehörige Livestream der abgespielt werden soll platziert werden.

Zu beachten gibt es:
-	Es werden nur mp3 Streams unterstützt
- Es werden keine https Streams unterstützt
- Die Streams müssen direkt via einem URL verfügbar sein, http-Umleitungen, sowie URL Parametisierung (Z.b. http://www.example.com/playback.mp3?Parameter1=Wert1&Parameter2=Wert2...) werden nicht unterstützt.

![2](/uploads/moh-livestream-helper/2.jpg "2")

## Wandeln nicht kompatibler Streams mit VLC


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
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung
