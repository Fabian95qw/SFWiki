---
title: MOH Livestream Helper
description: 
published: true
date: 2023-03-22T06:47:16.774Z
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
Platzieren sie im MPG123 Download URL den Downloadlink zur MPG123 Version als tar.bz2, die sie installieren wollen

Aktuelle URL's können unter: https://sourceforge.net/projects/mpg123/files/mpg123/ gefunden werden

Z.b. Aktuell hinterlegter URL. http://ufpr.dl.sourceforge.net/project/mpg123/mpg123/1.23.6/mpg123-1.23.6.tar.bz2

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
Wenn ein Stream nicht direkt kompatibel ist, so kann er mithilfe des Re-Streamings durch ein drittanbieter Programm kompatibel gemacht werden.

In diesem Beispiel wir der VLC Media Player verwendet.

Zuerst öffnet man den Original Stream in VLC.
Dann kan man ihn Rechtsklicken und "Stream" auswählen.
![3](/uploads/moh-livestream-helper/3.png "3")



Auf der nächsten Seite sollte die Quelle nun schon vorausgefüllt sein. Und man kann auf "Nächstes" drücken.
![4](/uploads/moh-livestream-helper/4.png "4")

Nun wird gefragt, was für eine Zielplattform fürs Streaming verwendet werden soll, hier muss auf "HTTP" geändert werden, und dann "Hinzufügen".
![5](/uploads/moh-livestream-helper/5.png "5")

Nun kann man noch Anpassungen bezgl. Streamingport und Streamingverzeichnis machen. Wenn hier die Standardwerte nicht angepasst werden, ist der Stream unter http://\[IP-des-Geräts\]:8080 erreichbar.
![6](/uploads/moh-livestream-helper/6.png "6")

Wichtig ist, dass der Stream zu mp3 Transkodiert wird, ansonsten kann MPG123 diesen nicht lesen.
![7](/uploads/moh-livestream-helper/7.png "7")

Auf der letzten Seite kann nun der Stream gestartet werden. Oben werden im Textfeld noch die Command Line Argumente dargestellt, wenn man dieses Stream-Konfiguration mit einer Quelle zu einem späteren Zeitpunkt per CMD starten will.
![8](/uploads/moh-livestream-helper/8.png "8")

Um den Stream zu starten muss man nun im Player die neue Datei "Converting \[Streamname\]" anklicken". Der VLC Stream sollte danach still sein, aber unten Links sollte die Zeit trotzdem hochzählen. Das heisst, der Stream läuft erfolgreich.
![9](/uploads/moh-livestream-helper/9.png "9")

Um zu prüfen, ob der Stream läuft, kann nun der Streamurl in einem Webbrowser aufgerufen werden, wenn man einen Unendlich langen Download erhält, läuft der Stream auf diesem Port, und der URL kann so ins Modul übernommen werden.
![10](/uploads/moh-livestream-helper/10.png "10")

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
