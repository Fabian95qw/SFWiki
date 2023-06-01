---
title: IQueue dynamische Optionen
description: 
published: true
date: 2023-06-01T07:19:49.245Z
tags: 
editor: markdown
dateCreated: 2023-05-31T09:10:56.210Z
---

# Beschreibung
Das Modul passt basierend auf der Anzahl Agenten in einer IQueue gewisse Werte wie z.b. "Maximale Länge der Queue" oder "Maximale Verweildauer" an

# Konfiguration

## Mögliche Anzupassende Werte
Das Modul erlaubt es folgende Werte anzupassen:

- Maximale Länge der Queue
- Maximale Verweildauer
- Klingeldauer
- Klingelpause
- Nachbearbeitungszeit

> Wenn andere, nicht vom Modul gedeckte Werte in der IQueue editiert werden soll, muss das Modul vorab deaktiviert werden, da es sonst zu einem Konflikt beim editieren der IQueue kommen kann, und die Änderungen ggf. verworfen werden, da das Modul zwischenzeitlich "durch einen anderen Benutzer" editiert wurde{.is-warning}


Bei jedem Wert gibt es jeweils die gleichen Optionen, deshalb wird das ganze nur einmal beschrieben.

## Zu Überwachende Gruppe

Die Gruppe, dessen Konfiguration überwacht wird. Es muss ich hierbei um eine IQueue Gruppe handeln, und die Anlage muss Lizenzen für IQueue Gruppen enthalten.

![1.PNG](/uploads/dynamic-iqueue-config/1.PNG)


Das Modul Zählt folgende Mitglieder als "Aktive" Agenten:

- Agent ist an aktiv Gruppe angemeldet
- Agent hat kein DND

## Modus

Man kann jeweils einen von 3 Modus festlegen.

![2.PNG](/uploads/dynamic-iqueue-config/2.PNG)


### Modus: -
Dieser Wert wird vom Modul nicht angefasst

### Modus: Tabelle
Der Wert wird basierend auf der Tabelle gesetzt.
Wenn ein Wert in der Tabelle nicht exisitiert, wird der nächst Tiefer angelegt Wert gewählt.

#### Beispiel

Wenn 7 Agenten in der Gruppe wären, würde hier der Wert von 5 Agenten zählen, es würde somit die Maximale Länge der Queue auf 15 ansetzen.

![3.PNG](/uploads/dynamic-iqueue-config/3.PNG)

### Modus: Erhöhung pro Agent mit positivem Wert

In diesem Modus wird folgende Formel für die Kalkulierung angewendet:
\[Minimalwert\]+(\[Anzahl Agenten\] \* \[Wert für dynamische Erhöhung\])

![4.PNG](/uploads/dynamic-iqueue-config/4.PNG)

### MinimalWert / Maximalwert
Dies Verhindert, dass diese Formel unendlich skaliert.
Man möchte z.b. die Verweildauer nicht ins Unendliche verlängern.

#### Beispiel
Der Wert für die dynamische Erhöhung ist auf 30 Sekunden gesetzt. 
Der Minimalwert ist: 60
Der Maximalwert ist 600
Es gibt 40 Agenten in der Gruppe

Dies würde folgendes Ergebnis bringen: 60 + (40\*30) ==> 1260 Sekunden ==> 21 Minuten.
Dies würde also die Verweildauer von Kunden auf 21 Minuten setzen, wenn es nicht druch den Maximalwert Limitiert wäre. Aber da dieser gesetzt ist, würde die Verweildauer aber auf 10 Minuten gesetzt.

![4.PNG](/uploads/dynamic-iqueue-config/4.PNG)

### Modus: Erhöhung pro Agent mit negativem Wert
Wenn der Wert für die dynamische Erhöhung auf einen negativen Wert gesetzt wird Ändert sich die Formel wie folgt:
\[Maximalwert\]+(\[Anzahl Agenten\] \* \[Wert für dynamische Erhöhung\])

#### Beispiel
Der Wert für die dynamische Erhöhung ist auf -5 Sekunden gesetzt. 
Der Minimalwert ist: 30 Sekunden
Der Maximalwert ist 60 Sekunden
Es sind 3 Agenten in der Gruppe.

Dies würde folgendes Ergebnis bringen: 60 + (3\*-5) ==> 45 Sekunden
Dies heisst, die Klingelzeit pro Benutzer reduziert sich um 5 Sekunden, je mehr Agenten angemeldet sind, bis auf ein Minimum von 30 Sekunden.

![5.PNG](/uploads/dynamic-iqueue-config/5.PNG)


# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung