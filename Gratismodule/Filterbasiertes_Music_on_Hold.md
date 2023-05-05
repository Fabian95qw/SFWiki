---
title: Zeit- & Filter-basiertes Music on Hold
description: 
published: true
date: 2023-05-05T09:34:38.355Z
tags: 
editor: markdown
dateCreated: 2021-09-27T12:13:36.391Z
---

# Beschreibung
Dieses Modul erlaubt es die Warteschlangenmsuik für eingehende Anrufer Zeitgesteuert, sowie basierend auf Filter für die Anrufer & Angerufene Nummer zu setzen.

> IQueue Wartschlangen können nicht überschrieben werden.
{.is-danger}


# Konfiguration

![moh-config.png](/uploads/music-on-hold/moh-config.png)

## Vorrang
Wenn nun bei einem Szenario einerseit, eine Anrufer, sowie Angerufene Nummer für einen Anrufer zutrifft, muss entschieden werden, welche Music-On-Hold verwendet wird.

Z.b.
Der Kunde Ruft mit 0041 123 45 67 in der Firma Muster auf die Rufnummer 0049 987 65 43 an.

Der Anrufer Filter besagt, dass alle Anrufer aus der Schweiz die Wartschlangenmusik "Jodeln" erhalten, jedoch ist definiert, dass alle die auf die Rufnummer 0049 987 65 43 Anrufen die Warteschlange "Schlager" erhalten sollen.

Je nach Vorrang, wird nun die "Jodeln" oder "Schlager" Warteschlangenmusik gesetzt

## Zeiträume
Es können Zeiträume definiert werden, in denen dieses spezifische Konfiguration gilt. 
Das Format hier, ist genau gleich wie bei der [Zeitgesteuerten Umleitung von STARFACE](https://knowledge.starface.de/pages/viewpage.action?pageId=46566379) aber nur in Deutsch

## Filtermöglichkeiten

![moh-filter.png](/uploads/music-on-hold/moh-filter.png)

Mögliche Formate:
00491234567890 ==> Exakte Nummer
0049123456* ==> Alle Nummern die mit 0049123456 beginnen
\*789 ==> Alle Nummern die mit 789 Aufhören
\*123\* ==> Alle Nummern die 123 irgendwo in der Nummer enthalten
12\. ==> Alle dreistelligen Nummern, die mit 12 beginnen
\.23 ==> Alle dreistelligen Nummern, die mit 23 aufhören
\.2\. ==> Alle dreistelligen Nummern, die mit einem Beliebigen Zeichen beginnen, eine zwei in der Mitte haben, und mit einem Beliebigen zeichen Aufhören.
\... ==> Alle dreistelligen Nummern
\.23\* ==> Alle Zahlen, die mit einer Zahl beginnen, darauf mit 23 Folgen, und danach mit Beliebig vielen Zeichen aufhören 


# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung