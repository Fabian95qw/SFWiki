---
title: Statusgesteuerte Besetztlampenfelder
description: 
published: true
date: 2022-10-17T12:20:24.040Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:37:04.000Z
---

# Beschreibung
Das Modul überwacht den Chatstatus einer Gruppe von Starface Usern, und setzt ggfs. bei Änderungen am Status die Besetztlampenfelder auf Rot. Z.B. wenn ein Teilnehmer abwesend ist, wird seine BLF automatisch Rot.

# Konfiguration
![Stateblf 1](/uploads/stateblf/stateblf-1.png "Stateblf 1")

## Statusreaktion
Im Modul muss eine Gruppe angegeben werden. Das Modul wird dann nur den Status jedes Mitglieds der Gruppe überwachen.
Ausserdem muss man Anhaken, auf welche Status genau reagiert werden soll.

## Statustexte
Es kann zusätzlich zum Status noch definiert werden, auf welche Texte reagiert werden soll.
Z.b. soll nur auf "Abwesend" mit dem Text "Ausser Haus" reagiert werden.

# Beispiel
![Stateblf 2](/uploads/stateblf/stateblf-2.gif "Stateblf 2")
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung