---
title: Erweiterte CallerID
description: 
published: true
date: 2023-11-10T13:20:50.911Z
tags: 
editor: markdown
dateCreated: 2023-11-10T13:11:19.580Z
---

# Beschreibung
Dieses Modul überschreibt die Standard CallerID der STARFACE mit den in den Modul Konfigurierten, sofern der Benutzer im STARFACE internen Adressbuch existiert

# Konfiguration

## Timeout
Während der Anruf aufgelöst wird, wird dieser im Modul gehalten, und es klingelt nicht. Dies definiert, wie lange das Modul maximal auf die Antworten der Adressbücher wartet, bevor es den Anruf unaufgelöst weiterleitet.


## STARFACE Benutzer für Adressbuchsuche
Damit das Adressbuch durchsucht werden kann, muss ein Benutzer mitgegeben werden, der Benutzer benötigt keine speziellen Anforderungen

## Zu durchsuchende Adressbücher
Definiert welche STARFACE Adressbücher durchsucht werden sollen, dies ist entweder:
- Die Adressbuchnummer 1-10
- all: Für das Adressbuch 0
- private: Für die privaten Adressbücher aller User
- users: Für die STARFACE Benutzer

## Zu durchsuchende Adressbücher bei LDAP Anbindung
- Bei der LDAP Anbindung müssen als Suchbegriffe die LDAP SearchBases hinterlegt werden Z.b. dc=starface,dc=pbx

## Mögliche Werte für CallerID
Offiziell sind nur Folgende Werte für die CallerID unterstützt:

| Wert      | Inhalt                                                   |
|-----------|----------------------------------------------------------|
| firstname | Vorname des Kontakts                                     |
| lastname  | Nachname des Kontakts                                    |
| company   | Firmenname des Kontakts                                  |
| number    | Die Rufnummer des Kunden vollständig Internationalisiert |

InOffiziell gibt es noch folgende Werte:

<details>
  <summary>Liste (Klicken zum Anzeigen)</summary>
  
  		academic_title,
		birthday,
		city,
		city2,
		city3,
		comment,
		company,
		country,
		country2,
		country3,
		email,
		email2,
		familyname,
		fax,
		faxshort,
		fax2,
		fax2short,
		fax3,
		fax3short,
		fax_caller_id,
		firstname,
		homephone,
		homephoneshort,
		job_tilte,
		messager,
		messager2,
		mobile,
		mobileshort,
		mobile2,
		mobile2short,
		mobile3,
		mobile3short,
		phone,
		phone2,
		phone3,
		phone4,
		phone5,
		phone6,
		phone7,
		phoneshort,
		phone2short,
		phone3short,
		phone4short,
		phone5short,
		phone6short,
		phone7short,
		phonetype,
		pobox2,
		pobox3,
		postcode,
		postcode2,
		postcode3,
		state,
		street,
		street2,
		street3,
		title,
		url,
		url2,
  
</details>

## Formatierung CallerID

Die CallerID wird entsprechend diesem Feld Formatiert. Werte, die durch Kontaktinformationen ersetzt werden sollen müssen in Raute gepakt werden.

Z.b.: #lastname# #firstname# #company# (#number#)
Erzeugt:




## Maximale Zeichenlänge der Werte

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung