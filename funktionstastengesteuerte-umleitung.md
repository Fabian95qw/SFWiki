---
title: Funktionstastengesteuerte Umleitung
description: 
published: true
date: 2021-08-16T11:01:55.157Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:33:49.736Z
---

# Beschreibung
Bei jedem Teilnehmer sind mehrere Umleit-Tasten definierbar mit unterschiedlichen Zielen, unabhängiger Konfiguration von internen- und Direktwahl-Nummern 
# Konfiguration
## Definition des Quellbenutzers
![2](/uploads/funktionstastengesteuerte-umleitung/2.jpg "2")

Die einzelnen Instanzen des Moduls müssen jeweils einem Benutzer/Gruppe zugewiesen werden.

### Interne Nummernlänge
Man muss dem Modul Mitteilen, wie lange die internen Rufnummern sind, damit er diese von den externen Rufnummern unterscheiden kann.

### Umleitung setzen für:
Hier kann man wählen, ob die Umleitung für einen Benutzer, oder eine Gruppe ist.

### Gruppenumleitungen des Benutzers miteinbeziehen 	
Im Falle, dass die Umleitung für einen Benutzer gewählt wird, werden dessen Gruppenumleitungen miteinbezogen.

### Nur ein Aktives Modul pro Benutzer/Gruppe erlauben
Wenn dieser Punkt aktiviert wird, dann kann ein Benutzer/Grupe immer nur eine aktive Instanz des Moduls haben.
Z.b. wenn ein Benutzer die Instanz "Uml. Zentrale" aktiv hat, und per BLF die Instanz "Uml. Voicemail aktiviert, wird die "Uml Zentrale" automatisch deaktiviert.

### Nur neue Umleitungsziele setzen
Wenn dieses Häkchen aktiviert ist, werden die neuen Umleitungsziele gesetzt, aber an dem Aktivierungsstatus der einzelnen Umleitungen wird nichts geändert. 

## Konfiguration der Umleitungen
Für die Konfiguration der Umleitungen gibt es 3 Tabs. Jede nachdem, ob man die Umleitung **Immer/Besetzt/Zeitüberschr**. setzen will.

![3](/uploads/funktionstastengesteuerte-umleitung/3.jpg "3")

### Nummern umleiten zu 
Definiert die Art des Ziels, es können Benutzer, Gruppen, Voicemailbox, oder Rufnummern gewählt werden.
**Zu beachten, bei der Voicemailbox, wird einfach der Punkt "Voicemailbox" aktiviert, und die dahinter Konfigurierte Box verwendet.**

### Umleitungsziele:
Bie den Umleitungszielen wird zwischen Internen/Externen zielen unterschieden.
Man kann also pro Konfiguration einmal Ziele für die internen, sowie externen Rufnummenziele setzen.
# Beispiel
![1](/uploads/funktionstastengesteuerte-umleitung/1.gif "1")
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung