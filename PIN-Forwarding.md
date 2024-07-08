---
title: PIN-Forwarding
description: 
published: true
date: 2024-07-08T08:12:48.038Z
tags: 
editor: markdown
dateCreated: 2024-04-26T08:00:04.375Z
---

# Beschreibung
Das Modul liest in regelmässigen Abständen eine .CSV Datei mit PIN-Forwarding Regeln ein.
Die PIN-Forwarding Regel besteht aus zwei Teilen, einem PIN, und einer SetNummer.
Ein Set kann für verschiedene Datum/Uhrzeiten wie die Zeitgest. Umleitung entsprechende Ziele enthalten.
Wenn das Modul angerufen wird, so soll ein Text abgespielt werden, dass den Anrufer zur PIN-Eingabe auffordert.
Der Anrufer gibt dann einen PIN mit \[n\] stellen per DTMF-interaktion ein.
Das Modul prüft, ob dieser PIN in der zuvor eingelesenen CSV exisitert.
Wenn der PIN exisitert, wird der Anrufer zum passenden Zielnummer im Entsprechenden Set basierend des Datums/Uhrzeits weitergeleitet.
Wenn der PIN nicht exisitert, oder der Anrufer keinen Vollständigen PIN in \[n\] Sekunden eingibt, wird der Anruf an eine Failover Nummer weitergeleitet.

# Konfiguration

![1.png](/uploads/pin-forwarding/1.png)

## DTMF & Fehlschlag
![2.png](/uploads/pin-forwarding/2.png)
Hier wird definiert, wie lange die PIN's maximal sein dürfen. Und wohin bei einem Fehlschlag die Nummer weitergeleitet wird.

## Audio
![3.png](/uploads/pin-forwarding/3.png)
Die zwei Audioansagen, welche das Modul abspielt. Einmal bei die Aufforderung zur PIN-Eingabe, sowie bei einem Fehlschlag.

## CSV Format

Die CSV Datei muss eine zweispaltige CSV-Datei sein, welche Links den PIN und Recht das Set enthält.

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

## Pin zu Set Mapping

### PIN-Set Mapping
![5.png](/uploads/pin-forwarding/5.png)
Hier wird das aktuelle Mapping für PIN <==> Set dargestellt. 
Hier können bei bedarf auch Manuell weitere PIN's zu Nummernmappings hinzugefügt werden.

## Sets
Im Modul können bis zu 10 Sets definiert werden, die den PIN's zugewiesen werden können.

## Set-Allgemeines
![6.png](/uploads/pin-forwarding/6.png)

## Einzelne Sets
![7.png](/uploads/pin-forwarding/7.png)

### Set Standard Ziel
Dieses Ziel wird verwendet, wenn kein Zeitraum im Set Zutrifft.

### Set Mapping
Die Zeiträume fürs Mapping können gemäss Syntax der [Zeitgesteuerte_Umleitung++](https://wiki.si-solutions.ch/de/Gratismodule/Zeitgesteuerte_Umleitung++) verwendet werden.

### Set Prioritäten
Wenn zwei Zeiträume in Konflikt stehen, müssen mir Prioritäten gearbeitet werden hierzu muss der Zeitraum um ein #1 Priorität erweitert werden, wobei 1 die höchste Priorität ist.
Z.b.

| Zeitraum | Ziel |
|---|---|
| 08.07.2024#1 | 200 |
| 01.07.2024-31.07.2024#3 | 300 |
| Montag#2 | 400 |

In dem Fall wäre am Montag dem 08.07.2024 das Ziel die 200.
Sonst im Datumsbereich 01.07.2024-31.07.2024 das Ziel die 300, ausser am Montag, dort ist das Ziel dann die 400.

### Set Upload
Hier wird die CSV Datei für dieses Set hochgeladen.

#### CSV Format
Das CSV Format für die Sets muss Zweispalting sein.
In der ersten Spalte muss jeweils der Zeitraum/Zeitraum#Priorität hinterlegt werden, und in der zweiten Spalte die Zielnummer.

Wenn für mehrere Zeiträume die gleiche Zielnummer gelten soll, so müssen mehrere Spalten mit dem gleichen Ziel definiert werden.

### Set Modus
Hier wird bestimmt, ob das Set geleert wird, und neu ab der Datei eingelesen wird, oder ob es mit der bestehenden Tabelle zusammengeführt wird.

### Upload verwenden.
Ist dies nicht aktiviert, so wird die .CSV Datei für dieses Set nicht eingelesen.

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung