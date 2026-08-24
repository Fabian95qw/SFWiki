---
title: Letzte Anrufer (Ab STARFACE 10.X)
description: 
published: true
date: 2026-08-24T10:04:58.191Z
tags: 
editor: markdown
dateCreated: 2026-08-24T09:51:25.485Z
---

# DSGVO
> Dieses Modul verstösst Standardmässig gegen das Datenschutzgesetz, da es einen begrenzten Einblick in die Rufhiestore von anderen Benutzern der Anlage liefert.
> 
> Es muss ein Schriftliches Einverständnis von den Benutzern der Anlage eingeholt werden, bevor dieses Modul genutzt werden darf.
{.is-warning}

# Beschreibung
Es gibt Kunden, bei denen eine Vielzahl von Mitarbeitern direkt mit der Hauptrufnummer raustelefonieren, und keine Direktwahl Anzeigen.

Hier gibt es immer wieder Fälle, bei denen dann Kunden zurückrufen, und Fragt, wer sie gesucht hat.
Die Zentrale kann selten direkt den korrekten Mitarbeiter gerade rausgeben, und muss entweder Rumfragen, oder den Kunden vertrösten, dass sich der Mitarbeiter wieder Meldet.

Dieses Modul/Widget soll dieses Problem lösen.
Mit diesem Modul lassen sich die letzten [n] Benutzer der STARFACE Anzeigen, welche die Zielnummer/Kunden zuletzt angerufen hatten, wenn dieser zurückruft.

![8.PNG](/uploads/lastcaller/8.PNG)


# Konfiguration

![9.PNG](/uploads/lastcaller/9.PNG)

## Länge der History
Definiert, wie viele Einträge ausgegeben werden sollen.

## Webseiten-URL
Der Webseiten URL wird für das Widget benötigt. Dies wird weiter unten im Detail erklärt.

## Passwortschutz Webseite 	
Hier muss ein Passwort für den Zugriff auf die Webseite definiert werden, dieses wird später beim Widget erzeugen benötigt.

# Widget erzeugen
  
![10.PNG](/uploads/lastcaller/10.PNG)

Es wird der Webseiten URL Benötigt und das Passwort, welches im Modul hinterlegt wurde.

In meinem Beispiel nehme ich den URL: http(s):<zero-width space/>//\[STARFACE]/downloads/f486/index.html

Und das Passwort: Test1234

Der URL muss um 3 Parameter erweitert werden einmal mit dem Füllwert von der STARFACE-App für Anruferinformationen (callerid) sowie dem Passwort und dem Namen der Instanz.

Der URL muss am schluss so aussehen:

http(s):<zero-width space/>//\[STARFACE]/downloads/f486/index.html?vcallerid=$(callerId)&modulekey=\[Passwort aus Modul\]&instancename=\[Name der Instanz\]

In meinem Beispiel:

https:<zero-width space/>//testface<zero-width space/>.si-solutions<zero-width space/>.ch/downloads/41f1/index.html?vcallerid=$(callerId)&modulekey=Test1234&instancename=LetzteAnrufeSISolutions

Dieser URL kann dann in den UCC-Client eingepflegt werden.

![6.PNG](/uploads/lastcaller/6.PNG)

Wenn nun alles korrekt ist, müsste das ganze in der STARFACE App so aussehen, wenn jemand Anruft, der zuvor bereits mal ausgehend Angerufen wurde.

![7.gif](/uploads/lastcaller/7.gif)

# Eigenes Design / Logo
Um ein eigenes Design oder Logo zu verwenden kann das Standard-Webseitenpaket editiert und hochgeladen werden.

Dieses gibts zum Download unter: https://module.si-solutions.ch/lastcaller/Standard-Webseitenpaket.zip
Die Struktur innerhalb der .ZIP Datei muss erhalten bleiben, damit es Ordnungsgemäss funktioniert.
Das Logo findet man im Unterordner "img/logo.png".

Alternativ kann auch die .SFM Datei mit einem Programm wie z.b. Winrar/7Zip geöffnet werden, und das Logo im "res/62948e86-026f-45d9-96a5-076de39487b2.zip" ersetzt werden.

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung