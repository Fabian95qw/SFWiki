---
title: Music on Hold Konfigurations Editor
description: 
published: false
date: 2022-07-11T09:26:25.033Z
tags: 
editor: markdown
dateCreated: 2022-07-08T09:53:07.797Z
---

# Beschreibung
Dieses Modul ermöglicht es die MusicOnHold.conf aus der STARFACE oberfläche zu editieren.


# Konfiguration

![config.png](/uploads/music-on-hold-config-editor/config.png)

## Music on Hold Konfiguration laden

![loadconfig.png](/uploads/music-on-hold-config-editor/loadconfig.png)

Bevor eine Konfiguration editiert werden kann, muss die bestehende Konfiguration der Warteschlange in das Modul geladen werden.

Dafür muss zu oberst der Warteschlangenname hinterlegt werden.

> Das Modul muss anschliessend gespeichert (nicht übernommen) werden. Ansonsten können die Werte vom Config file nicht in die GUI geschrieben werden.
{.is-warning}

## Music on Hold Konfiguration editieren/speichern
![writeconfig.png](/uploads/music-on-hold-config-editor/writeconfig.png)

Wenn das Modul die Konfiguration der Warteschlange geladen hat, kann man die Werte editieren, oder neue Wert hinzufügen.

In dem Beispielbild oben wird der neue Schlüsel "sort" mit dem "wert" Random hinzufügt. 
Dies erzeugt den Eintrag "sort=random" im Music On Hold Config file. Somit

## Duplicate Keys umgehen

![keyduplicate.png](/uploads/music-on-hold-config-editor/keyduplicate.png)

Gewisse Werte können in der Music on Hold Config mehrmals vorkommen. Jedoch verlangt die STARFACE in der GUI, dass der Schlüsselwert einzigartig ist.

Wenn mehrere Werte den gleichen Schlüssel haben, so können diese durch das Voransetzen von Doppelpunkten unterschieden werden.

Also z.b.

- entry = /var/lib/asterisk/sounds/en/yourcallisimportant
- :entry = http://example.local/sales-queue-hold-music.ulaw
- ::entry = /var/lib/asterisk/moh/macroform-robot_dity

Die vorausgehenden Doppelpunkte werden vor dem schreiben ins Configfile entfernt.

##

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung