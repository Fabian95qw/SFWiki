---
title: Quelle: Datei Importer
description: 
published: true
date: 2021-08-16T09:42:22.347Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:38:17.884Z
---

# Beschreibung
Hier geht es Spezifisch um die Konfiguration des Datei-Importers im Adressbuch Importer
# Konfiguration
## Import
![Datei Import 1](/uploads/adressbuch-importer/datei-import-1.png "Datei Import 1")
### Protkoll

Hier muss im Voraus das Protokoll festgelegt werden, dessen Konfiguration verwendet werden soll.

### Fileimportmodus

**Nur spezifisches CSV Importieren**
In diesem Modus wird nur ein Spezifisches CSV in dem in der Konfiguration angegebenen Pfad gesucht. Dieser muss weiter unten bei „Spezifischer Dateiname“ angegeben werden.

**Alle CSV’s Importieren**
Die Starface lädt alle Dateien mit der Endung .csv aus dem Ordner herunter. Und Importiert diese nacheinander.

**Neuste CSV Importieren**
Er lädt die neuste Datei mit der Endung .CSV herunter. Hierbei überprüft er den Wert der letzten Änderung (Siehe Artikel „Wikipedia Changed Date“)

**Spezifischer Dateiname**
Wird nur beim Fileimportmodus „Nur Spezifisches CSV Importieren“ benötigt. Dieser Dateiname wird hinten an den Konfigurierten FTP/SMB Pfad angehängt.

**Ignoriere erste Zeile**
Ignoriert die erste Zeile der CSV’s. Dies wird Z.B. benötigt, wenn die Spaltenbeschriftungen noch vorhanden sind. 
Template für Importdateien
Beim Export der Adressen aus anderen Programmen sind diese nicht unbedingt gerade Starface Konform Formatiert, deshalb kann man ein eigenes Template für eigene Imports einspielen.

**Trennzeichen**
Das definierte Trennzeichen für die CSV-Datei

**Charset**
Das vorausgesetzte Encoding der CSV-Datei

##  Template
 
###  Eigenes Template verwenden
Das eigene Template für den Import verwenden. Wenn dieses hochgeladen wurde
  
### Beispiel Template

**Beispieldaten aus Applikation XY**

![Vorlageappxy](/uploads/adressbuch-importer/vorlageappxy.png "Vorlageappxy")

Diese sollen in die Starface Importiert werden. Hierfür kann ein Template generiert werden.
Als Vorlage für das Template benutzen wir die CSV-Import Vorlage der Starface:

![Template](/uploads/adressbuch-importer/template.png "Template")

Die darin enthaltenen Spaltennamen werden von der Starface erkannt.

Wir platzieren nun die Header in den Spalten, die den entsprechenden Spalten im ApplikationXY.csv Entsprechen:

![Vorlageresult](/uploads/adressbuch-importer/vorlageresult.png "Vorlageresult")

**Das Resultierende Template muss im CSV Format Semicolon ( ; ) getrennt & im UTF-8 Format abgespeichert werden.**

In diesem Fall würde der „rohe“ CSV-Code so aussehen:

> [LEER];Name [contact:familyname];Vorname [contact:firstname];;Firma [contact:company];PLZ [address:postcode];Straße [address:street];;Rufnummer [telephone:phone]

Dies kann so in den Menüpunkt „Eigenes Template“ hochgeladen werden. Somit verwendet diese Modulinstanz beim Import dieses Template, um die Kontakte korrekt zu interpretieren.
 
# http(s) Get
##  HTTPS 
Die http(s) get Funktion erlaubt es eine CSV. Von einem Webhost abzurufen. 

### 302 URL redirection Erlauben 		
Erlaubt eine Umleitung von der URL während des Importprozesses. Für mehr Infos siehe: https://en.wikipedia.org/wiki/HTTP_302

### GET Request URL		
Der Request URL.** Ohne Protokoll!**
Beispielsweise: meinhost.meinestadt.de/kontakte/adressen.csv?user=test&amp;password=[PASSWORT]

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
Dies ist der Import Pfad zum Adressbuch. Er muss mit einem Slash („/“) beginnen und im letzten Ordner ohne Backslash aufhören. 
Ein Dateiname darf nicht angehängt werden. (Dieser wird oben im Import gesetzt)
 
# SMB-Konfiguration
## SMB Status
Dieses Feld gibt Feedback, ob die aktuelle Konfiguration in Ordnung ist. Dieser Wert wird beim Abspeichern des Moduls vom System überschrieben.

## SMB Import Pfad
Dies ist der Import Pfad zum Adressbuch. Er muss mit einem Slash („/“) beginnen und im letzten Ordner ohne Slash aufhören. Ein Dateiname darf nicht angehängt werden. (SIEHE Import)

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung