---
title: Statusgesteuerte Umleitung
description: 
published: true
date: 2025-10-08T08:30:59.809Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:37:23.912Z
---

# Beschreibung
Das Modul überwacht den Chatstatus einer Gruppe von Starface Usern, ändert sich nun der Status eines Users z.b. auf "Abwesend" ändert, sowie aktiviert das Modul Umleitungen vom Typ "Immer, Besetzt, Zeitüberschreitung" (Konfigurierbar) 
# Konfiguration
## Überwachung
![stateredirect](/uploads/stateredirect/stateredirect-1.png "stateredirect-1")
### Interne Nummernlänge
Man muss dem Modul Mitteilen, wie lange die internen Rufnummern sind, damit er diese von den externen Rufnummern unterscheiden kann.

### Zu Überwachende Gruppe
Die Gruppe, dessen Mitglieder überwacht werden soll

> Der User muss aktiv in der Gruppe angemeldet sein!
{.is-warning}


### Gruppenumleitungen des Benutzers miteinbeziehen 	
Im Falle, dass die Umleitung für einen Benutzer gewählt wird, werden dessen Gruppenumleitungen miteinbezogen.

## Statusreaktion
### Vordefinierte Status
Es sind einige Status, auf die Reagiert werden kann bereits vordefiniert. Diese müssen nur Angehakt wereden.

### Eigene Statustexte
Es gibt die Möglichkeit eigene Statustexte, auf die Reagiert werden soll in der Liste einzutragen.
Hierbei kann * als Wildcard verwendet werden.

Z.b. "In den Ferien bis \*"

## Ergebnis
![stateredirect](/uploads/stateredirect/stateredirect-2.gif "stateredirect-2")
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung