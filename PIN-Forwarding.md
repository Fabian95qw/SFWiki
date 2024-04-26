---
title: PIN-Forwarding
description: 
published: false
date: 2024-04-26T08:16:01.883Z
tags: 
editor: markdown
dateCreated: 2024-04-26T08:00:04.375Z
---

# Beschreibung
Das Modul liest in regelmässigen Abständen eine .CSV Datei mit PIN-Forwarding Regeln ein.
Die PIN-Forwarding Regel besteht aus zwei Teilen, einem PIN, und einer Zielnummer.
Wenn das Modul angerufen wird, so soll ein Text abgespielt werden, dass den Anrufer zur PIN-Eingabe auffordert.
Der Anrufer gibt dann einen PIN mit \[n\] stellen per DTMF-interaktion ein.
Das Modul prüft, ob dieser PIN in der zuvor eingelesenen CSV exisitert.
Wenn der PIN exisitert, wird der Anrufer zur dahinterliegenden Nummer weitergeleitet.
Wenn der PIN nicht exisitert, oder der Anrufer keinen Vollständigen PIN in \[n\] Sekunden eingibt, soll der Anruf an eine Failover Nummer weitergeleitet werden.

# Konfiguration

![1.png](/uploads/pin-forwarding/1.png)

## DTMF & Fehlschlag
![2.png](/uploads/pin-forwarding/2.png)
Hier wird definiert, wie lange die PIN's maximal sein dürfen. Und wohin bei einem Feschlag die Nummer weitergeleitet wird.

## Audio
![3.png](/uploads/pin-forwarding/3.png)
Die zwei Audioansagen, welche das Modul abspielt. Einmal bei die Aufforderung zur PIN-Eingabe, sowie bei einem Fehlschlag.

## Upload der CSV Datei
![4.png](/uploads/pin-forwarding/4.png)

### Modus
Beim Modus wird bestimmt wie mit den bestehenden PIN's umgehen soll.

#### Zusammenführen.
Die neuen PIN's werden mit den bestehenden PIN's zusammegenführt:

- Neue PIN's werden hinzugefügt
- Bei bestehenden PIN's wird das Ziel überschrieben

#### Alte PIN's löschen.
Die PIN-Tabelle wird komplett geleert und nur mit den neuen PIN's bestückt.

### CSV-Trennzeichen.
Das Trennzeichen, welches die .CSV Datei verwendet.

### Testdatei
Neben dem Laden ab der STARFACE Festplatte kann per Upload eine CSV Datei für Testzwecke hochgeladen werden, sofern der Haken "Testdatei verwenden" aktiviert ist.

> Diese Daten werden mit den Daten ab der Festplatte zusammengeführt. wobei bei Doppelten PIN's die Daten ab der Festplatte vorrang haben.
{.is-warning}

### Pfad ab Festplatte
Der Pfad auf der Festplatte, welche zur .CSV Datei führt.

> Diese Datei wird jedes mal geladen, wenn das Modul gespeichert wird, und wenn der Timer konfiguriert ist.
{.is-info}

> Zur korrekten Anwendung der Datei muss das Modul immer gespeichert (Nicht übernommen) werden!
{.is-danger}

### Intervall zum Laden ab Festplatte.
In welchem Zeitraum die .CSV ab der Festplatte neu eingelesen werden soll.

## Mapping
![5.png](/uploads/pin-forwarding/5.png)
In einem Separaten Tab wird noch das aktuelle PIN - Nummernmapping dargestellt. 
Hier können bei bedarf auch Manuell weitere PIN's zu Nummernmappings hinzugefügt werden.

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung