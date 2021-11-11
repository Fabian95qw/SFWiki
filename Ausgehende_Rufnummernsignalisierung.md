---
title: Ausgehende Rufnummernsignalisierung
description: 
published: true
date: 2021-11-11T15:50:29.453Z
tags: 
editor: markdown
dateCreated: 2021-08-27T09:55:24.018Z
---

# Beschreibung
Das Modul ermöglicht es die Rufnummernsignalisierung von Benutzer mit möglichen Quell, sowie Zielnummernfiltern zu setzen.

# Wahl der Logik
Das Modul kann zwei verschiedene Logiken: Nummernmapping mit Filtermöglichkeit, oder Nummernfilter mit einer CallerID.

## Nummernmapping mit Filtermöglichkeit

![1.PNG](/uploads/zielabhaengige-rufnummernsignalisierung/1.PNG)

### Zu reagierende Gruppe
Es werden nur auf Teilnehmer dieser Gruppe reagiert.

> Falls keine Gruppe gewählt wird, werden auf alle augehenden Anrufe reagiert.
{.is-danger}

### Vorrang
Wenn nun bei einem Szenario einerseit, eine Benutzerdefinierte Rufnummer, sowie eine Zieldefinierte Rufnummer zutrifft, muss gesetzt werden, welche Vorrang hat.

Z.b.
Für den Benutzer 100, ist als anzuzeigende Rufnummer die 0041 234 56 78 gesetzt, jedoch ruft er die Zielnummer 041 595 10 60, für welche teil des Filters 0041* ist. Für diesen Filter ist die Anzeigenummer 0041 786 54 32 gesetzt.

Je nach Vorrang, wird er nun die 0041 234 56 78 bzw. 0041 786 54 32 gegen aussen Anzeigen.

### Filtermöglichkeiten
Mögliche Formate:
00491234567890 ==> Exakte Nummer
0049123456* ==> Alle Nummern die mit 0049123456 beginnen
*789 ==> Alle Nummern die mit 789 Aufhören
*123* ==> Alle Nummern die 123 irgendwo in der Nummer enthalten
12. ==> Alle dreistelligen Nummern, die mit 12 beginnen
.23 ==> Alle dreistelligen Nummern, die mit 23 aufhören
.2. ==> Alle dreistelligen Nummern, die mit einem Beliebigen Zeichen beginnen, eine zwei in der Mitte haben, und mit einem Beliebigen zeichen Aufhören.
... ==> Alle dreistelligen Nummern
.23* ==> Alle Zahlen, die mit einer Zahl beginnen, darauf mit 23 Folgen, und danach mit Beliebig vielen Zeichen aufhören 

### Benutzerbasiertes Nummernmapping
Hier können anzuzeigende Rufnummern basierend auf Einzelnummern, Nummernbereichen usw. gesetzt werden.

Beim Filtern werden jeweils Folgende Felder berücksichtigt
Primäre interne Rufnummer des Benutzers
Primäre externe Rufnummer des Benutzers
Seine jetzige Signalisierte Rufnummer

### Zielbasiertes Nummernmapping
Hier können anzuzeigende Rufnummern basierend auf der Gewählten Zielnummer gesetzt werden.
Zu beachten ist, die Nummern müssen im korrekten internationalisierten Format verwendet werden.
> Internationale Vorwahlen müssen immer das 00 verwenden, ansonsten funktioniert der Filter nicht.
{.is-danger}

## Nummernfilter mit einer CallerID
![2.png](/uploads/zielabhaengige-rufnummernsignalisierung/2.png)

### Zu reagierende Gruppe
Es werden nur auf Teilnehmer dieser Gruppe reagiert.

> Falls keine Gruppe gewählt wird, werden auf alle augehenden Anrufe reagiert.
{.is-danger}

### Zu setzende CallerID
Die CallerID, die für alle gesetzt wird, die dem Filter entsprechen

### Filtermöglichkeiten
Mögliche Formate:
00491234567890 ==> Exakte Nummer
0049123456* ==> Alle Nummern die mit 0049123456 beginnen
*789 ==> Alle Nummern die mit 789 Aufhören
*123* ==> Alle Nummern die 123 irgendwo in der Nummer enthalten
12. ==> Alle dreistelligen Nummern, die mit 12 beginnen
.23 ==> Alle dreistelligen Nummern, die mit 23 aufhören
.2. ==> Alle dreistelligen Nummern, die mit einem Beliebigen Zeichen beginnen, eine zwei in der Mitte haben, und mit einem Beliebigen zeichen Aufhören.
... ==> Alle dreistelligen Nummern
.23* ==> Alle Zahlen, die mit einer Zahl beginnen, darauf mit 23 Folgen, und danach mit Beliebig vielen Zeichen aufhören 

### Zielummern Filtern mit Black-/Whitelist
Dieses gibt einem die Möglichkeit, 


# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung