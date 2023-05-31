---
title: IQueue dynamische Optionen
description: 
published: false
date: 2023-05-31T09:28:11.121Z
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

Wenn 7 Agenten in der Gruppe wäre, würde hier der Wert von 5 Agenten zählen, es würde somit die Maximale Länge der Queue auf 15 ansetzen.

![3.PNG](/uploads/dynamic-iqueue-config/3.PNG)

### Erhöhung pro Agent






# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung