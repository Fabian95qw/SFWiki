---
title: TOTP 2 Login
description: 
published: true
date: 2024-02-22T12:21:28.472Z
tags: 
editor: markdown
dateCreated: 2023-12-11T14:52:57.457Z
---

# Beschreibung
Dieses Modul ermöglicht es, die Anmeldung an Telefonen mithilfe von \*77 mit einem Zeitbasierten Einmalcode abzusichern.

# Einloggen
Die Benutzer, müssen sich nach aktivierung des Moduls an den Tischtelefonen neu via \*77\[LoginID\]\*\[Einmalpasswort\] einloggen.

# Konfiguration

![1.PNG](/uploads/totp2login/1.PNG)

## TOTP aktivieren für
Bestimmt ob das TOTP für \*77 für alle Benutzer oder eine Gruppe von Benutzern aktiviert werden soll.

## Gruppe für TOTP
Die Gruppe, für welche die TOTP aktiviert werden soll


> Benutzer müssen einen TOTP Code eingeben, solange sie in der Tabelle "Benutzer und Secrets" noch vorhanden sind, selbst, wenn sie zwischenzeitlich nicht mehr Mitglied der Gruppe sind. Damit sie keinen Code mehr eingeben müssen, muss ihre LoginID manuell aus der Tabelle gelöscht werden.
{.is-danger}


## TOTP-Einstellungen

### Secret-Länge
Wie lange das TOTP-Secret sein soll.

### PIN-Länge
Wie Lange der TOTP-PIN im Authenticator sein soll

### Gültigkeit des PINs \[s\]
Wie viele Sekunden ein TOTP Code jeweils gültig seins oll.

### Erlaubte vorherige/zukünftige PINs mit Zeitdiskrepanz 	

Wenn sich die zeit Zwischen dem TOTP Gerät und der STARFACE unterscheidet, so kann ein Code, welcher auf dem TOTP Gerät generiert wurde auf der STARFACE bereits nicht mehr gültig, oder noch nicht gültig sein. Z.b. bei einer Gültigkeit von 60 Sekunden, und eine Diskrepanz von 1 kann der Code von 1 Minute vorher, sowie 1 Minute in der Zukunft ebenfalls verwendet werden. Bei einer Diskrepanz von 0 ist nur der aktuell dargestellte Code gültig

### TOTP-App Label
Die Beschriftung des TOTP-Generators in der TOTP App

### Herausgeber
Der Herausgeber, welcher in der TOTP App dargestellt werden soll

### Algorithmus, welcher für die Generierung des TOTP Codes verwendet wird.

## E-Mail Versand

![2.PNG](/uploads/totp2login/2.PNG)

### QR Code Name
Name des QR-Code .png's welches an den E-Mails angehängt wird

### Name des Absenders
Namen des Absenders vom E-Mail

### E-Mail Titel
Der Titel vom E-Mail

### E-Mail Text
Der Text, welcher im E-Mail hinterlegt wird. Dieser wird als .txt Datei benötigt.

#### Standard E-Mail Text
Guten Tag meine Damen und Herren

Angehängt finden sie den QR-Code für das Einrichten eines TOTP (Zeit basierter Einmal-Passwort). 
Dieser wird für die Anmeldung an Tischtelefonen via \*77\#loginid\#\*\[Einmalpasswort\] benötigt.

Bitte Scannen sie den angehängten QR-Code mit einer Authenticator App wie z.b. Google Authenticator, oder Microsoft Authenticator um ihm zu nutzem.

Für mehr Inforamtionen wenden sie sich bitte an ihren Administrator.

### QR-Code für jeden neuen Teilnehmer per E-Mail senden 	
Wenn das Modul abgespeichert wird, wird geprüft, ob es noch neue Secrets zu generieren gibt, wenn ja, generiert es diese, und sendet den Benutzer anschliessend die E-Mail mit dem QR-Code.

### Alle QR-Codes nochmals versenden
Sendet allen Benutzern den QR-Code nochmals zu.

### Alle QR Codes an eine spezifische Adresse senden
Sendet alle QR-Codes an die bei "Ziel E-Mail Adresse" hinterlegte E-Mail

### Einzelnen QR Code an eine spezifische Adresse senden
Sendet den bei "QR-Code für" definierten QR-Code an die bei "Ziel E-Mail Adresse" hinterlegte E-Mail.

## Auto-Generierte Secrets
Die Tabelle enthält die Generierten Secrets der User gemäss den TOTP-Einstellungen.
Diese Secrets können auch von Hand in Authenticator Apps eingepflegt werden.

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung