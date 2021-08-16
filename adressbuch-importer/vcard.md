---
title: Quelle: VCard
description: 
published: true
date: 2021-08-16T09:42:45.683Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:39:12.400Z
---

# Beschreibung
Hier geht es Spezifisch um die Konfiguration des VCard-Importes im Adressbuch Importer
# Konfiguration
 ![Vcard](/uploads/adressbuch-importer/vcard.png "Vcard")
# http(s) Get
##  HTTPS 
Die http(s) get Funktion erlaubt es eine VCard. Von einem Webhost abzurufen. 

### 302 URL redirection Erlauben 		
Erlaubt eine Umleitung von der URL während des Importprozesses. Für mehr Infos siehe: https://en.wikipedia.org/wiki/HTTP_302

### GET Request URL		
Der Request URL.** Ohne Protokoll!**
Beispielsweise: meinhost.meinestadt.de/kontakte/adressen.vcf?user=test&amp;password=[PASSWORT]

### [PASSWORT] Variable 
Ermöglicht das Verstecken von Passwörter innerhalb des URLs . 
Das Wort [PASSWORT] wird innerhalb der URL wä;hrend des Vorangs mit dem Passwort beschrieben. Z.B. www.test.ch/adressen.csv?user=test&amp;password=[PASSWORT]
Request Ergebnis
 
### Request Ergebnis
Das Request Ergebnis gibt das Ergebnis des letzten http(s) Requests zurück. Also Z.b. 404 not found.

# FTP-Konfiguration
## FTP Status
Dieses Feld gibt Feedback, ob die aktuelle Konfiguration in Ordnung ist. Dieser Wert wird beim Abspeichern des Moduls vom System überschrieben.
## FTP Import Pfad
Dies ist der Import Pfad zum Adressbuch. Er muss mit einem Backslash („\“) beginnen und im letzten Ordner ohne Backslash aufhören. 
Ein Dateiname darf nicht angehängt werden. (Dieser wird oben im Import gesetzt)
 
# SMB-Konfiguration
## SMB Status
Dieses Feld gibt Feedback, ob die aktuelle Konfiguration in Ordnung ist. Dieser Wert wird beim Abspeichern des Moduls vom System überschrieben.

## SMB Import Pfad
Dies ist der Import Pfad zum Adressbuch. Er muss mit einem Slash („/“) beginnen und im letzten Ordner ohne Slash aufhören. Ein Dateiname darf nicht angehängt werden.  (Dieser wird oben im Import gesetzt)

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung
