---
title: Add-On: Funktionstasten aktualisieren
description: 
published: true
date: 2021-05-25T10:00:23.422Z
tags: 
editor: markdown
dateCreated: 2021-04-07T12:27:42.682Z
---

# Beschreibung

Ein Modul, welches die Funktionstaste einer Gruppe von Benutzern aktualisiert.
Das Modul nimmt die Namen und Vornamen der Benutzer auf der STARFACE, und prüft ob die dazugehörigen Besetztlampenfelder noch korrekt beschriftet sind.

Falls nicht, korrigiert das Modul diese wieder basierend auf den Moduleinstellungen.

# Konfiguration

![funktionstaste-aktualisieren-1.png](/uploads/funktionstasten-aktualisieren/funktionstaste-aktualisieren-1.png)

## Automatische Ausführung
Das Modul kann diesen vorgang in gewissen Intervallen ausführen (Z.b. einmal Täglich)

### Automatisieren
Die Automatische ausführung passiert nur, wenn dieser Haken aktiviert ist

### Telefone provisionieren
Bestimmt, ob die Tischtelefone auch neu provisioniert werden soll!
**Achtung, je nach Tischtelefonw ird dieses neu gestartet**

## Parametisierung Besetztlampenfelder

### Länge Vor/Nachname
Bestimmt, wieviele Zeichen des Vor und Nachnamens angezeigt werden sollen. 
**Eine Zeichenlänge von 0 entspricht dem vollständigen Namen**
Beispiel: 
Name: Max Mustermann
Länge Vorname:1
Länge Nachname:6
Ergibt: M Muster

### Zielgruppe
Bestimmt, bei welchen Usern die Funktionstasten mit dem Modul bearbeitet/korrigiert wird.
**Wenn keine Gruppe gewählt wurde, werden alle STARFACE Benutzer aktualisiert**

### Funktionstastenbeschriftung
Um möglichst alle Formatwünsche abdecken zu können, kann man das Format der Besetztlampenfelder Freihändig bestimmen.
Die Variablen:
- ##LASTNAME## 
- ##FIRSTNAME##
- ##INTERNALNUMBER##
 werden durch die Entsprechenden Daten des Benutzers ersetzt.
 
Beispiele: 
Name: Max Mustermann
Länge Vorname:1
Länge Nachname:6
Format: ##FIRSTNAME##.##LASTNAME##|##INTERNALNUMBER##
Ergibt: M.Muster|123

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch/de/lizenzierung