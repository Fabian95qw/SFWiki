---
title: Zeitgesteuerte Umleitung ++
description: 
published: false
date: 2023-01-05T14:25:37.115Z
tags: 
editor: markdown
dateCreated: 2023-01-05T13:59:29.102Z
---

- # Beschreibung
Das Zeitgesteuerte Umleitungsmodul++ ist eine Eigenentwicklung, welche gewisse Verbesserungen gegenüber dem Originalen Zeitgest. Umleitungsmodul mit sich bringt.

Dies Enthält u.a.:

- Datumsbereiche mit dynamischen Jahr (yyyy statt dem Jahr angeben)
- Die CallerID verändern um ihn so als Umgeleitet zu "Markieren"
- Definieren, ob es innerhalb, oder ausserhalb des Zeitfensters passieren soll.
- Konfigurationen können exportiert & importiert werden, so kann man z.b. eine Vorlage Datei erstellen, welche man bei verschiedenen Kunden importieren kann.

# Konfiguration

## Interne Anrufe ingorieren
Ignoriert Anlageninterne Anrufe

> Vorsicht Anrufe über den Anlagenverbund zählen nicht dazu
{.is-warning}

## CallerID Erweitern
Sagt, ob die CallerID erweitert werden soll
Wenn ja, wird sie um den Entsprechenden Präfix & Suffix erweitert.
Z.b. mit einem Präfix von "Uml. " und einem Suffix von \[E\] würde aus "Max Mustermann" "Uml. Max Mustermann\[E\]

# Nummernfilter
Es muss definiert werden, auf welche Anrufer & Angerufene Nummern reagiert wird.
Dazu gibt es folgende Filtermöglichkeiten:

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

## Nummer des Anrufers Filter & Ausnahmen
Filter, welche hier gesetzt werden, werden auf die Nummer des Anrufers angewendet.

Er Prüft folgende Nummern:
- Externe Rufnummer des Anrufers
- Interne Rufnummer des Anrufers (Falls vorhanden)
- IFMC Rufnummer des Anrufers (Falls vorhanden)

## Nummer des Angerufenen Filter & Ausnahmen
Filter, welche hier gesetzt werden, werden auf die Angerufene Nummer angewendet.

# Zeiten
Hier werden die Zeitfenster in denen reagiert, oder nicht reagiert werden soll, definiert.

## Reaktion
Bestimmt, ob das Modul Innerhalb, oder ausserhalb des Zeitfensters reagiert.

## Sprache von Datum/Uhrzeit
Hier wird definiert, in welcher SPrache, die Zeiten im Zeitplan eingetragen werden.

## Zeitplan
Hier werden die Entsprechenden Zeiten definiert.

### Beispiele
01.06.2018-30.06.2018 ==> Gilt ab dem 01.06.2018 bis 30.06.2018 (00:00 Uhr bis 23:59 Uhr)
24.12.yyyy-31.12.yyyy ==> Jedes Jahr vom 24.12 bis zum 31.12
15.06.2018 ==> Gilt am gesamten 15.06.2018 von 00:00 Uhr bis 23:59 Uhr
01.01.yyyy ==> Jedes Jahr am 01.01
Mo ==> Gilt an jedem Montag von 00:00 Uhr bis 23:59 Uhr
Samstag-Sonntag ==> Gilt an jedem Samstag und Sonntag von 00:00 Uhr bis 23:59 Uhr
12:00-13:00 ==> Gilt jeden Tag von 12:00 Uhr bis 13:00 Uhr
Samstag 12:00-14:00 ==> Gilt jeden Samstag von 12:00 Uhr bis 14:00 Uhr 

# Ziele
Es muss auch ein Ziel definiert werden, an welches das Modul weitergeleitet wird.

## Rufnummer / Mailbox (\*9)
Der Ruf wird an diese Nummer, oder Voicemailbox weitergeleitet. Bei Voicemailboxen muss die Nummer inkl. dem \*9 präfix eingegeben werden

## Ansage
Spielt eine Ansage ab, und hängt den Anruf anschliessend auf

## Ansage + Rufnummer / Mailbox(\*9)
Eine Kombination der zwei oberen.

## Benutzer
Anruf wird an einen Benutzer weitergeleitet

## Gruppe
Anruf wird an eine Gruppe weitergeleitet.

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung