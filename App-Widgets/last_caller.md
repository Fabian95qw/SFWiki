---
title: Letzte Anrufer
description: 
published: true
date: 2023-10-05T06:17:41.139Z
tags: 
editor: markdown
dateCreated: 2023-10-02T09:54:02.418Z
---

# Beschreibung
Es gibt Kunden, bei denen eine Vielzahl von Mitarbeitern direkt mit der Hauptrufnummer raustelefonieren, und keine Direktwahl Anzeigen.

Hier gibt es immer wieder Fälle, bei denen dann Kunden zurückrufen, und Fragt, wer sie gesucht hat.
Die Zentrale kann selten direkt den korrekten Mitarbeiter gerade rausgeben, und muss entweder Rumfragen, oder den Kunden vertrösten, dass sich der Mitarbeiter wieder Meldet.

Dieses Modul/Widget soll dieses Problem lösen.
Mit diesem Modul lassen sich die letzten [n] Benutzer der STARFACE Anzeigen, welche die Zielnummer/Kunden zuletzt angerufen hatten, wenn dieser zurückruft.

![8.PNG](/uploads/lastcaller/8.PNG)


# Konfiguration

![1.PNG](/uploads/lastcaller/1.PNG)

## Länge der History
Definiert, wie viele Einträge ausgegeben werden sollen.

## Webseiten-URL
Der Webseiten URL wird für das Widget benötigt. Dies wird weiter unten im Detail erklärt.

## Tokengenerator-URL
Unter diesem URL ist der Tokengenerator für das Widget erreichbar.
Dieser wird für die Widgeterzeugung benötigt.

# Widget erzeugen

## Token für Widget generieren
Bevor das Widget eingebunden werden kann, muss der Tokengenerator unter dem im Modul erzeugten Link aufgerufen werden.

![3.PNG](/uploads/lastcaller/3.PNG)

In diesem Beispiel ist der Link: http(s):<zero-width space/>//\[STARFACE\]/downloads/f486/tokengen/index.html

 Dort müssen alle Felder mit den Informationen der STARFACE + einem Login ausgefüllt werden.
  
![5.PNG](/uploads/lastcaller/5.PNG)

Dies Erzeugt dann einen fertigen Token im untersten Feld. Dieser muss kopiert werden.
Für das obenliegende Beispiel würde dieser so aussehen: https%3A%2F%2Ftestface.<zero-width space/>si-solutions<zero-width space/>.ch%2Fxml-rpc%3Fde.vertico.starface.auth%3D100%3A5123899fe5a452123aeff5217816c06a6f8c85e499e40351426a6855381af44b6584eb9391761960506c081d713876261686d8d5fa3fa96470adb5c6943fead9

![4.PNG](/uploads/lastcaller/4.PNG)

Dieser muss dann mit dem Webseiten-URL Kombiniert werden, in meinem Beispiel: http(s):<zero-width space/>//\[STARFACE]/downloads/f486/index.html

Der URL muss um 2 Parameter erweitert werden einmal mit dem Füllwert von der STARFACE-App für Anruferinformationen (callerid) sowie dem generierten Token.

Der URL muss am schluss so aussehen:

http(s):<zero-width space/>//\[STARFACE]/downloads/f486/index.html?vcallerid=$(callerId)&sfrequrl=\[Token vom Tokengenerator]

In meinem Beispiel:

https:<zero-width space/>//testface<zero-width space/>.si-solutions<zero-width space/>.ch/downloads/f486/index.html?vcallerid=$(callerId)&sfrequrl=https%3A%2F%2Ftestface.<zero-width space/>si-solutions<zero-width space/>.ch%2Fxml-rpc%3Fde.vertico.starface.auth%3D100%3A5123899fe5a452123aeff5217816c06a6f8c85e499e40351426a6855381af44b6584eb9391761960506c081d713876261686d8d5fa3fa96470adb5c6943fead9

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