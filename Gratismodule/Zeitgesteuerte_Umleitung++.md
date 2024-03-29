---
title: Zeitgesteuerte Umleitung ++
description: 
published: true
date: 2024-03-14T14:32:00.163Z
tags: 
editor: markdown
dateCreated: 2023-01-05T13:59:29.102Z
---

- # Beschreibung
Das Zeitgesteuerte Umleitungsmodul++ ist eine Eigenentwicklung, welche gewisse Verbesserungen gegenüber dem Originalen Zeitgest. Umleitungsmodul mit sich bringt.

Dies Enthält u.a.:

- Datumsbereiche mit dynamischen Jahr (yyyy statt dem Jahr angeben)
- Die CallerID verändern (Präfix/Suffix) um den Anruf so als Umgeleitet zu "Markieren"
- Definieren, ob es innerhalb, oder ausserhalb des Zeitfensters passieren soll.
- Konfigurationen können exportiert & importiert werden, so kann man z.b. eine Vorlage Datei erstellen, welche man bei verschiedenen Kunden importieren kann.

# Konfiguration

![1.PNG](/uploads/zeitgesteuerte_umleitung_si/1.PNG)

## Interne Anrufe ingorieren
Ignoriert Anlageninterne Anrufe

> Vorsicht Anrufe über den Anlagenverbund zählen nicht dazu
{.is-warning}

## CallerID Erweitern
Sagt, ob die CallerID erweitert werden soll
Wenn ja, wird sie um den Entsprechenden Präfix & Suffix erweitert.
Z.b. mit einem Präfix von "Uml. " und einem Suffix von \[E\] würde aus "Max Mustermann" "Uml. Max Mustermann\[E\]

> Module, welche die CallerID Formatieren (Z.b. eine Rückwärttsuche, oder lookup in externen DB) stehen in dem Modul konflikt, und es kann sein, dass die CallerID wieder überschrieben wird. 
Bitte beachten sie entsprechend die Ausführreihenfolge der Module.
{.is-warning}

# Nummernfilter
Es muss definiert werden, auf welche Anrufer & Angerufene Nummern reagiert wird.
Dazu gibt es folgende Filtermöglichkeiten:

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

## Nummer des Anrufers Filter & Ausnahmen

![2.PNG](/uploads/zeitgesteuerte_umleitung_si/2.PNG)

Filter, welche hier gesetzt werden, werden auf die Nummer des Anrufers angewendet.

Er Prüft folgende Nummern:
- Externe Rufnummer des Anrufers
- Interne Rufnummer des Anrufers (Falls vorhanden)
- IFMC Rufnummer des Anrufers (Falls vorhanden)

## Nummer des Angerufenen Filter & Ausnahmen
Filter, welche hier gesetzt werden, werden auf die Angerufene Nummer angewendet.

![3.PNG](/uploads/zeitgesteuerte_umleitung_si/3.PNG)

# Zeiten
![4.PNG](/uploads/zeitgesteuerte_umleitung_si/4.PNG)

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
![5.PNG](/uploads/zeitgesteuerte_umleitung_si/5.PNG)

Es muss auch ein Ziel definiert werden, an welches das Modul weitergeleitet wird.

## Rufnummer / Mailbox (\*9) / 302 Call Deflection
Der Ruf wird an diese Nummer, oder Voicemailbox weitergeleitet. 
Bei Voicemailboxen muss die Nummer inkl. dem \*9 präfix eingegeben werden
Bei 302 Call Deflection wir der Anruf per SIP 302 weitergeleitet.

## 302 Call Deflection
Folgendes wird beim 302 Call Deflection angegeben:

| Header   | Wert                             |
|----------|----------------------------------|
| orig-num | Originale Rufnummer des Anrufers |
| from-num | Angerufene Rufnummer             |
| to-num   | Die Zielnummer gemäss Textfeld   |

> Bei gewissen Providern muss 302 Call-Deflection zuerst vom Provider freigegeben werden.
{.is-warning}

> Mit 302 Umgeleitete Anrufe tauchen immer als verpasste Anrufer mit einer Zeit von 0 Sekunden in der STARFACE auf.
{.is-danger}


## Ansage
Spielt eine Ansage ab, und hängt den Anruf anschliessend auf

## Ansage + Rufnummer / Mailbox(\*9) 
Eine Kombination der zwei oberen.

## Benutzer
Anruf wird an einen Benutzer weitergeleitet

## Gruppe
Anruf wird an eine Gruppe weitergeleitet.


# Auto-Deaktivierung
Das Modul kann sich nun zu einem gewissen Zeitpunkt selbt deaktivieren, falls Konfiguriert.
Damit lassen sich z.b. Fälle abdecken, wenn ein User eine Spezielle Umleitung aktiviert, und diese am nächsten Morgen aber spätestens wieder deaktiviert sein soll.

![7.PNG](/uploads/zeitgesteuerte_umleitung_si/7.PNG)

# Konfigurationen Exportieren/Importieren
![6.PNG](/uploads/zeitgesteuerte_umleitung_si/6.PNG)

Das Modul kann die Einstellungen per E-Mail Senden, und man kann sie wieder zurück in die Instanz laden.

> Die Exportdatei ist ein Serialisierter Java Objectstream. 
Auch wenn sie auf den ersten Blick lesbar aussieht, sollte sie auf keinem Fall von Hand editiert werden.
{.is-danger}


## Exportieren
Für den Export muss die E-Mail Adresse ausgefüllt werden, und der haken bei "Konfiguration per E-Mail senden" gesetzt sein. Man erhält dann eine \[UUID\].sfinstance. 

Die Datei kann ohne Probleme umbenannt werden. Die Endung .sfinstance muss aber behaltet werden!

## Importieren
Zum Importieren muss man einfach die .sfinstance Datei hochladen, unten den Haken "Konfiguration Importieren" Anhaken, **und das Modul Abspeichern (nicht Übernehmen)!**


# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung