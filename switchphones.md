---
title: Arbeitsplatzwechsel
description: 
published: true
date: 2023-12-13T10:46:51.861Z
tags: 
editor: markdown
dateCreated: 2023-12-13T10:09:20.694Z
---

# Beschreibung

Das Modul soll es ermöglichen, per Tastendruck am Telefon zwischen "Standorten" zu wechseln und zu definieren, welche Telefone je nach "Standort" klingeln sollen. 
Z.b. bei einer Taste "Homeoffice, soll das Bürotelefon nicht mehr klingeln, sondern nur noch das Softphone, und das Primärtelefon soll entsprechend umgestellt werden"
Wenn nun die Taste wieder deaktiviert wird, soll das Büro wieder klingeln, und das Primärtelefon zurückgestellt werden.

Es soll zusätzlich die Möglichkeit gegeben werden, diese Einstellungen Zeitgesteuert wieder anzuwenden, z.b. dass um Mitternacht die Einstellungen wieder aufs Büro zurückgestellt werden.

![1.gif](/uploads/switchphones/1.gif)

# Konfiguration

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

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung