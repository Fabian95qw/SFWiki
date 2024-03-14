---
title: Ausgehende Black-/White-list
description: 
published: false
date: 2024-03-14T14:31:53.438Z
tags: 
editor: markdown
dateCreated: 2024-03-14T14:19:58.605Z
---

# Ausgehende Black-/White-list
Ausgehende Anrufe für Gruppen von Benutzern mit einer Black-/White-list mit Wildcard Filtern einschränken. Inkl. E-Mail Alarmierung bei Verstössen.

# Konfiguration

## Zu Limitierende Gruppe
Es werden **alle** Mitglieder Gruppe überprüft, **egal ob sie Aktiv/Inaktiv** sind. 

## Interne Anrufe ignorieren
Das Modul kann auch interne Rufe gegen den Filter prüfen, falls gewünscht. Wenn der Haken aktiviert ist, werden interne Anrufe vom Modul generell ignoriert.

## Modus Blacklist/Whitelist
Bestimmt in welchem Modus der Filter Arbeitet.
Im Blacklist Modus werden alle beim Filter gesetzte Nummern Blockiert, ausser die Ausnahmen.
Im Whitelist Modus werden alle Anrufe blockiert, welche nicht auf dem Filter sind. 
Zusätzlich werden Anruf Blockiert, welche auf dem Filter sind aber bei den Ausnahmen vorkommen.

## Filter & Ausnahmen
Hier können Nummern mithilfe von Wildcards platziert werden.

### Filtermöglichkeiten
Mögliche Formate:
00491234567890 ==> Exakte Nummer
0049123456\* ==> Alle Nummern die mit 0049123456 beginnen
\*789 ==> Alle Nummern die mit 789 Aufhören
\*123\* ==> Alle Nummern die 123 irgendwo in der Nummer enthalten
12\. ==> Alle dreistelligen Nummern, die mit 12 beginnen
.23 ==> Alle dreistelligen Nummern, die mit 23 aufhören
.2. ==> Alle dreistelligen Nummern, die mit einem Beliebigen Zeichen beginnen, eine zwei in der Mitte haben, und mit einem Beliebigen zeichen Aufhören.
... ==> Alle dreistelligen Nummern
.23\* ==> Alle Zahlen, die mit einer Zahl beginnen, darauf mit 23 Folgen, und danach mit Beliebig vielen Zeichen aufhören 

## Verstösse Senden
Wenn aktiviert, sendet das Modul bei einem Verstoss eine E-Mail an die Zieladresse.
Der Titel des E-Mails Lautet: \[Datum im Format dd.MM.yy HH:mm\] Verstoss gegen Filter!
Der Textinhalt des E-Mails Lautet:
Datum: \[Datum im Format dd.MM.yy HH:mm\]
Anrufer: \[Vorname\] \[Nachname\] \[LoginID\]
Angerufen: \[Vollständige Internationalisierte Rufnumer\]
