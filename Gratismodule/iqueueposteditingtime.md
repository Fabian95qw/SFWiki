---
title: IQueue mehr Nachbearbeitungszeit
description: 
published: true
date: 2023-07-25T09:42:44.325Z
tags: 
editor: markdown
dateCreated: 2023-07-25T09:21:02.421Z
---

# Beschreibung
Ein Modul zum Ändern/Setzen der Nachbearbeitungszeit für einzelne Benutzer.

# Konfiguration

![1.PNG](/uploads/iqueueposteditingtime/1.PNG)

## Rufnummernzuweisung

Das Modul benötigt zwei Rufnummern:
- Eine Rufnummer, um die Nachbearbeitungszeit des Anrufers zu erhöhen.
- Eine Rufnummer, um die Nachbearbeitung des Anrufers zu beenden.

Zur unterscheidung der Rufnummern, müssen diese im Modul eingetragen werden.

## IQueue für Nachbearbeitungszeit

Für welche IQueue Gruppe diesem Benutzer Nachbearbeitungszeit zugesprochen werden soll.

## Modus

### Dazuzählen
Nachbearbeitsungszeit neu = Rest der aktuellen Nachbearbeitungszeit + Nachbearbeitungszeit \[s\]

Beim Dazuzählen, wir die bestehende Nachbearbeitungszeit, welche der Benutzer hat dazugezählt.

Z.b.
Max Mustermann hat eine Nachbearbeitungszeit von 60 Sekunden. Er hat bereits 30 Sekunden verbraucht, und weiss, dass er mehr Zeit benötigt.
Das Modul Rechnet ihm nun weitere 60 Sekunden dazu, das heisst, die neue Restnachbearbeitungszeit wäre 90 Sekunden.

### Setzen
Nachbearbeitungszeit neu = Nachbearbeitungszeit \[s\]

Es wird ihm erneut die im Modul definierte Nachbearbeitungszeit gewährt.

Z.b.
Max Mustermann hat eine Nachbearbeitungszeit von 60 Sekunden. Er hat bereits 30 Sekunden verbraucht, und weiss, dass er mehr Zeit benötigt.
Das Modul setzt seine Nachbearbeitungszeit wieder auf 60 Sekunden.

# Tasten Konfigurieren
Den Benutzern müssen zwei Tasten vom Typ "Direktwahl" platziert werden, die jeweils die entsprechende Rufnummer zum Ändern/Setzen der Nachbearbeitungszeit, sowie zum Beenden der Nachbearbeitung enthalten.

# Beispiel

![2.gif](/uploads/iqueueposteditingtime/2.gif)

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung