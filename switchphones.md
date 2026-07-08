---
title: Arbeitsplatzwechsel
description: 
published: true
date: 2026-07-08T08:04:27.916Z
tags: 
editor: markdown
dateCreated: 2023-12-13T10:09:20.694Z
---

# Beschreibung

Das Modul soll es ermöglichen, per Tastendruck am Telefon zwischen "Standorten" zu wechseln und zu definieren, welche Telefone je nach "Standort" klingeln sollen. 
Z.b. bei einer Taste "Homeoffice, soll das Bürotelefon nicht mehr klingeln, sondern nur noch das Softphone, und das Primärtelefon soll entsprechend umgestellt werden"
Wenn nun die Taste wieder deaktiviert wird, soll das Büro wieder klingeln, und das Primärtelefon zurückgestellt werden.

Es gibt zusätzlich die Möglichkeit, diese Einstellungen Zeitgesteuert wieder anzuwenden, z.b. dass um Mitternacht die Einstellungen wieder aufs Büro zurückgestellt werden.

# Modus
Hier muss zuerst der Modus gewählt werden, in dem das Modul funktioniert:

- durch Modul de-aktivierung
- durch Standorterkennung STARFACE App
- durch Telefonumstellung




![1.gif](/uploads/switchphones/1.gif)

# Modul de-aktivierung

![2.PNG](/uploads/switchphones/2.png)

## Benutzer
Der Benutzer, deren Telefone umgestellt werden sollen

## IFMC Telefone ignorieren
Ob IFMC Telefone vom Modul ignoriert werden sollen.

## Bei De-/Aktivierung des Moduls

### Primärtelefon umstellen auf
Bestimmt, welches Telefon als Primärtelefon eingestellt werden soll.
Bei Softphone wird das Softphone (WinClient/MacClient) ausgewählt.
Bei Tischtelefon, wird das erste Nicht-Softphone ausgewählt.

> Wenn der Teilnehmer mehr als ein Softphone / Tischtelefon besitzt, muss man den Modus auf "Spezifisches Telefon nach Name" einstellen und den vollständigen SIP-Namen des Telefons eingeben, da sonst ggf. das Falsche Telefon vom Modul ausgewählt wird.
{.is-warning}

### Namen des Primärtelefons
Name des Primärtelefons, wenn die Auswahl auf "Spezifisches Telefon nach Name" steht.
Genau so wie im Benutzer unter "Telefone" zu finden
Z.b. SIP/2231.ylnkt54

### Andere Telefone
Bestimmt, was mit den anderen Telefonen passieren soll, wenn das Modul umgestellt wird.

- deaktivieren --> Deaktiviert alle anderen Telefone
- aktivieren --> Aktiviert alle anderen Telefone
- Aktivierung umkehren --> Aktiviert alle deaktivierten Telefone und deaktiviert alle aktivierten Telefone

## Modul automatisch deaktivieren
Deaktiviert das Modul zu einem gewissen Zeitpunkt wieder damit z.b. 
Das Modul um Mitternacht wieder vom Homeoffice aufs Büro umstellt.

# Standorterkennung

![3.PNG](/uploads/switchphones/3.png)

## Standorterkennung für:
Schränkt die Erkennung des Standorts ein.
Zur Verfügung stehen:

- Alle Benutzer
- Bestimme Gruppe von Benutzer
- Einzelner Benutzer

## IFMC Telefone ignorieren
Ob IFMC Telefone vom Modul ignoriert werden sollen.

## Formate Telefon
Für die Telefone können folgende Werte angegeben weden:

- Hardphone -> Das erste Tischtelefon des Benutzers
- Softphone -> Das Softphone des Benutzers
- Vollständiger Telefonname -> Z.b. 5390.ylnkt56
- Telefonname mit Wildcards -> Z.b. *.ylnkt*

## Standardtelefon wenn nichts Zutrifft.
Sollte keiner der Standorte Zutreffen, so wird automatisch auf dieses Telefon zurückgegriffen.
Unterstütz alle Formate für Telefone

## Standorterkennung DNS
Die STARFACE fragt die DNS-Namen ab, und merkt sich die dahinterliegenden IP's (Z.b. für Dyndns)
Wenn der Benutzer sich von diesem Standort aus an der App Anmeldet, wird das Telefon umgestellt.

## Standorterkennung IP/CDR
Wenn sich der Benutzer von diesem Subnetz Anmeldet, wird das Telefon entsprechend umgestellt.
Die Subnetze müssen immer im Format IP/SUBNET angegeben werden, z.b. 192.168.1.0/24.
Einzelne IP's müssen mit dem /32 Subnetz versehen werden.

# Telefonumstellung
In diesem Modus müssen die User das Modul über bestimmte Rufnummern Anrufen, um den entsprechenden User am Telefon anzumelden. 
Pro User muss hier dem Modul eine Direktwahl zugesprochen werden, welche dann als Taste auf das Telefon gelegt wird.

Der User der aktuell am Telefon ist wird abgemeldet und je nach Tabelle wird sein Telefon einem Dummy-User zugewiesen.

> Die Anmeldung erfolgt ganz ohne die PIN-Anfrage die z.b. bei einem normalen \*77\[Interne Nummer] erfolgt.
{.is-warning}

![4.PNG](/uploads/switchphones/4.png)

## User für abgemeldete Telefone
Wenn ein User in der Tabelle "Rufnummer zu LoginID mit Logout Telefone" ist, und sich an einem zweiten Telefon anmeldet, wird sein altes Telefon abgemeldet und diesem User angemeldet.

Die Idee ist es einen User zu haben, der alle Anmeldetasten auf dem Display hat, so dass sich dann ein neuer User via drücken einer Taste wieder anmelden kann.

## Rufnummer zu LoginID mit/ohne Logout Telefone
Links muss die Direktwahl des Moduls angegeben werden, und Rechts die LoginID des Users der dann dem Anzurufenden Telefon zugewiesen wird.

Wenn es in der Tabelle "mit Logout" eingetragen wird, werden sein alten Telefone automatisch dem "User für abgemeldete Telefone" zugewiesen.

Wenn es in der Tabelle "ohne Logout" eingetragen wird, wird lediglich das neue Telefon dem User zugewiesen.

> Wenn die Direktwahl in keiner Tabelle existiert kommt ein Besetztzeichen.
Ebenso, wenn die LoginID, die Rechts angegeben ist nicht existiert.
{.is-danger}


# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung