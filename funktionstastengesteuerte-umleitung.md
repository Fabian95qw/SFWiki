---
title: Funktionstastengesteuerte Umleitung
description: 
published: true
date: 2022-10-24T06:01:47.971Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:33:49.736Z
---

# Beschreibung
Bei jedem Teilnehmer sind mehrere Umleit-Tasten definierbar mit unterschiedlichen Zielen, unabhängiger Konfiguration von internen- und Direktwahl-Nummern 
# Konfiguration
## Grunddefinitionen & Filter
![2.png](/uploads/funktionstastengesteuerte-umleitung/2.png)

Die einzelnen Instanzen des Moduls müssen jeweils einem Benutzer/Gruppe zugewiesen werden.

### Interne Nummernlänge
Man muss dem Modul Mitteilen, wie lange die internen Rufnummern sind, damit er diese von den externen Rufnummern unterscheiden kann.

### Nummernfilter
Erlaubt es gewisse Rufnummern von der Umleitung auszuschliessen bzw. die Umleitung nur für gewisse Umleitungen zu sezten.

#### Filtermöglichkeiten
Der Filter unterstützt die Wildcards \* (beliebig viele Zeichen) sowie ? (ein beliebiges Zeichen)

Beispiele:
+41\*:Nur Nummern die mit +41 Beginnen
2??:Nur Nummern die, welche mit einer 2 Beginnen, und zwei weitere Zahlen enthalten.
???: Nur 3 Stellige Nummern
004112345678:Nur die Nummer 004112345678
+49\*80: Nur +49 er Nummer, die mit 80 aufhören 

## Ziel wählen

![3.png](/uploads/funktionstastengesteuerte-umleitung/3.png)

### Umleitung setzen für:
Hier kann man wählen, ob die Umleitung für einen Benutzer, oder eine Gruppe ist.

### Gruppenumleitungen des Benutzers miteinbeziehen 	
Im Falle, dass die Umleitung für einen Benutzer gewählt wird, werden dessen Gruppenumleitungen miteinbezogen.

### Auszuführender Benutzer
Mit der STARFACE 6.7.1 wurde ein neues Features "auszuführender User" hinzugefügt um Sicherzustellen, dass Umleitungen an Gruppen nur von authorisierten Mitarbeitern durchgeführt wird.
Deshalb muss nun bei der De-Aktivierung von Umleitungen für Gruppen ein Benutzer angegeben werden. Module können Umleitung für Gruppen nur noch im Namen eines Benutzers setzen
Die Umleitungseinstellungen der Gruppe werden also im Namen des auszuführenden Users ausgeführt. Wird dieses Feld nicht ausgefüllt, oder hat der auszuführende User kein Recht zum setzen der Umleitung für die Gruppe passiert nichts.

## Erweiterte Features

![4.png](/uploads/funktionstastengesteuerte-umleitung/4.png)

### Nur ein Aktives Modul pro Benutzer/Gruppe erlauben
Wenn dieser Punkt aktiviert wird, dann kann ein Benutzer/Grupe immer nur eine aktive Instanz des Moduls haben.
Z.b. wenn ein Benutzer die Instanz "Uml. Zentrale" aktiv hat, und per BLF die Instanz "Uml. Voicemail aktiviert, wird die "Uml Zentrale" automatisch deaktiviert.

### Nur neue Umleitungsziele setzen
Wenn dieses Häkchen aktiviert ist, werden die neuen Umleitungsziele gesetzt, aber an dem Aktivierungsstatus der einzelnen Umleitungen wird nichts geändert. 

## Konfiguration der Umleitungen
Für die Konfiguration der Umleitungen gibt es 3 Tabs. Jede nachdem, ob man die Umleitung **Immer/Besetzt/Zeitüberschreitend**. setzen will.

![4.png](/uploads/funktionstastengesteuerte-umleitung/5.png)

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