---
title: Gruppenmitschnitte
description: 
published: true
date: 2021-04-07T13:51:26.433Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:34:04.394Z
---

# Beschreibung
Das Modul zeichnet alle ein- und ausgehende Gespräche an Externe von bestimmten Benutzern auf. Interne Gespräche können auf Wunsch auch aufgezeichnet werden. Die Audio-Dateien werden automatisch auf ein externes Speichermedium kopiert resp. verschoben. 
# Konfiguration
## Mitschnitt der Gruppe
Damit das Modul überhaupt funktioniert, muss zuerst eine Gruppe zugewiesen werden.

Danach muss noch definiert werden, welche Anruftypen (Eingehend, Interne, Ausgehende) dass genau aufgezeichnet werden sollen.

![1](/uploads/gruppenmitschnitte/1.jpg "1")

## Alarme
Das Modul erlaubt die Alamierung im Falle von Fehlgeschlagener Uploads von der Starface zum FTP/SMB Server

## Speicherverbrauch
Das Modul stellt u.a. denn aktuellen Speicherverbrauch dar.
Einerseit den Speicherverbrauch "in Verwendung", welches dem Speicherverbrauch der aktuell aktiven Aufzeichnung entspricht, sowie den Transferordner, wo alle noch zu übertragenden Audiodateien liegen.

## Bereinigung
Manchmal bleiben Anrufaufzeichnungen "stecken", dies passiert, wenn Asterisk, trotz bereits beendetem Anruf das File nicht schliesst.
Mithilfe der Bereinigung, zwingt man das Modul, auch aktuell geöffnete Dateien in den Transferordner zu schieben.
**Dies sollte nicht im aktiven Betrieb, sondern zu Randzeiten ausgeführt werden, da sonst alle aktuell aktiven Aufzeichnungen beendet werden.**

Die Bereinigung lässt sich ausserdem Automatisiert ausführen.

## Ansage & DTMF vor Aufzeichnung

Das Modul bietet die Möglichkeit, direkt eine Ansage zu platzieren, mit welcher man den Anrufer über die Aufzeichnung Informiert.
Ausserdem kann man ihm die Möglichkeit geben, die Aufzeichnung abzulehnen.

**Wenn ein Anruf abgelehnt wird, wird dieser trotzdem im Reporting gespeichert (Sofern Reporting aktiviert ist)**

![2](/uploads/gruppenmitschnitte/2.jpg "2")

## Upload
Das Modul kann Dateien in Regelmässigen Abständen auf einem SMB/FTP Server hochladen, hier wird alles darum herum Konfiguriert.
**Alternativ Lassen sich alle Aufzeichnungen auch per E-Mail Senden.**

### Dateiformat
Alle Aufzeichnungsdateien werden grundsätzlich im Format: Aufnahme_[DATUM]_[UHRZEIT]_[VON]_[NACH].wav hochgeladen

### SMB/FTP-Status
Das Modul Tests regelmässig die SMB/FTP Verbindung, und Speichert das Resultat in der entsprechenden Statuszeile.
**Während das Modul geöffnet ist aktualisiert sich diese Zeile nicht.**

![3](/uploads/gruppenmitschnitte/3.jpg "3")

## Reporting
Das Reporting ist ein Minimalistisches CSV, welches Folgende Infos enthält:

* Anrufer
* Angerufener
* Gesprächsstart
* Gesprächszeit
* Zugehörige Aufzeichnung

![4](/uploads/gruppenmitschnitte/4.jpg "4")

### Beispiel

![Reporting](/uploads/gruppenmitschnitte/reporting.png "Reporting")
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch/de/lizenzierung
