---
title: Gesprächsbewertung
description: 
published: false
date: 2023-11-13T10:31:06.599Z
tags: 
editor: markdown
dateCreated: 2023-11-13T08:25:07.419Z
---

# Beschreibung
Dieses Modul erlaubt es nach einem Gespräch eine Bewertung für den Anruf abzugeben.

# Einschränkungen

> Wenn z.b ein IVR Modul vorgeschaltet ist, darf nicht die ext. Nummer des IVR's im Filter hinterlegt werden, sondern die interne Rufnummer der dahinterliegenden Gruppen
{.is-warning}

> Wenn Anrufe intern Weitervermittelt wurden, funktioniert dieses Modul nicht mehr, da das Modul die Kontrolle über den Anruf bei vermittlungen verliert und somit den Anruf für die Umfrage nicht mehr zurückkholen kann.
{.is-danger}

# Flow
![Flow.png](/uploads/callevaluation/Flow.png)

# Konfiguration

![1.PNG](/uploads/callevaluation/1.PNG)

## Gesprächsbwertung ausführen für
Setzt fest, wo das Modul eine Möglich Gesprächsbewertung zulässt.

### Filtermöglichkeiten
Mögliche Formate:
00491234567890 ==> Exakte Nummer
0049123456\* ==> Alle Nummern die mit 0049123456 beginnen
\*789 ==> Alle Nummern die mit 789 Aufhören
\*123\* ==> Alle Nummern die 123 irgendwo in der Nummer enthalten
12. ==> Alle dreistelligen Nummern, die mit 12 beginnen
.23 ==> Alle dreistelligen Nummern, die mit 23 aufhören
.2. ==> Alle dreistelligen Nummern, die mit einem Beliebigen Zeichen beginnen, eine zwei in der Mitte haben, und mit einem Beliebigen zeichen Aufhören.
... ==> Alle dreistelligen Nummern
.23\* ==> Alle Zahlen, die mit einer Zahl beginnen, darauf mit 23 Folgen, und danach mit Beliebig vielen Zeichen aufhören 


# Texte
![2.PNG](/uploads/callevaluation/2.PNG)

## Anzahl Texte
Aktuell bietet das Modul nur die möglichkeit, eine Begrüssung, drei Fragen und einen Schlusstext abzuspielen.
Falls mehr Fragen gewünscht sind Kontaktieren sie uns einfach kurz.

## Wartezeit pro Antwort
Definiert, wie lange auf jede einzelne DTMF Antwort gewartet wird.

## Anzahl DTMF pro Bewertung
Definiert wie viele DTMF Ziffern pro Bewertung abgegeben werden dürfen.

# Auswertung & Transfer

![3.PNG](/uploads/callevaluation/3.PNG)

## Ausgewertete Daten
Folgene Daten werden aktuell Ausgewertet:
- Angerufene Nummer
- Mitarbeiter, welcher den Anruf entgegengenommen hat (LoginID)
- Datum/Uhrzeit (gemäss in GUI definiertem Format)

Die Informationen über den Anrufer sind im Hintergrund verfügbar, werden aber nicht in die CSV Datei geschrieben.

## Transfer
Wenn der Transfer stattfindet, wird jeweils die .CSV Datei für diesen Tag Transferiert.

## Transferoption E-Mail
![4.PNG](/uploads/callevaluation/4.PNG)

## Transferoption FTP
![5.PNG](/uploads/callevaluation/5.PNG)

## Transferoption SMB
![6.PNG](/uploads/callevaluation/6.PNG)

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung