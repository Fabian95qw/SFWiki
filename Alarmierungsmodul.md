---
title: Alarmierungsmodul
description: 
published: true
date: 2024-03-18T09:17:44.551Z
tags: 
editor: markdown
dateCreated: 2024-02-05T14:05:22.843Z
---

# Beschreibung
Ein Simples Modul, welches nacheinander Rufnummern auf einer Liste versucht anzurufen.
Wenn ein Teilnehmer abnimmt, wird er dazu aufgeforert, eine Taste zu drücken, um den Alarm zu bestätigen, bevor er mit dem Anrufer verbunden wird.

# Konfiguration

![1.png](/uploads/alarmmodule/1.png)

![2.png](/uploads/alarmmodule/2.png)

## Modus Alarmieren solange Anrufer am Telefon ist
Das Modul klingelt so lange durch, wie der originale Anrufer am Telefon ist.

## Anrufer aufhängen und Alarm auslösen
Das Modul hängt den Originalen Anrufer sofort auf, und startet danach den Alarmruf, und spielt normal die Ansagen ab, welche im Modul hinterlegt ist.


## Wartemusik Anrufer
Die Musik, die dem Anrufer abgespielt wird, während er wartet, dass einer der zu Alarmierenden Rufnummern abnimmt

## Anzahl Versuche
Wie oft alle Rufnummern nacheinander angerufen werden, bevor der Anruf weiter an die bei "Bei Fehlschlag weiter zu Rufnummer" hinterlegte Rufnummer weitergeleitet wird

## Klingelzeit pro Rufnummer \[s\]
Wie viele Sekunden es pro Rufnummer Klingeln soll

## Zu Alarmierende Rufnummern
Die Rufnummern, welche nacheinander Angerufen werden sollen.
Externe Rufnummern müssen vollständig internationalisiert sein.

# Audiotexte
Es können div. Audiotexte hinterlegt werden.
Das drücken der DTMF Taste zu einem Belebigen Zeitpunkt innterhalb der Texte führt automatisch zu einer akzeptierten Eingabe!
Der Resttext wird dann übersprungen, und die zwei Teilnehmer werden sofort zusammengeschaltet.

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung