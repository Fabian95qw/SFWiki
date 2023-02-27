---
title: Abwurfplatz
description: 
published: true
date: 2023-02-27T15:57:54.559Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:33:08.231Z
---

# Beschreibung
Ermöglicht es Tabellarisch Abwurfplätze für Einzelnummern / Nummernbereiche zu definieren. Somit kann mehr als ein Abwurfplatz für ein Rufnummernblock definiert werden. 
Die Bereiche können mithilfe von Platzhaltern definiert werden.

# Konfiguration

![1](/uploads/abwurfplatz/1.png "1")


## Leere Gruppen abfangen
Das Modul reagiert neben nicht zugewiesenen Nummern, ebenfalls auf leere Gruppen. 
"Leere Gruppen" sind definiert als:

- Gruppen ohne Mitglieder
- Gruppen bei denen kein Mitglied aktiv (Angehakt ist)
- Gruppen bei denen alle aktiven Mitglieder DND geschalten haben

## Benutzer ohne Telefone abfangen
Das Modul kann zusätzlich noch Benutzer, ohne aktive Telefone abfangen.
Ein Benutzer zählt als "ohne Telefon" wenn:

- Dem Benutzer kein Telefon zugewiesen ist
- Alle Telefone des Benutzers Offline/Rot sind

> Benutzer mit IFMC Telefonen können diesen zustand nie erreichen.
{.is-warning}

## CallerID Präfix & Suffix
Das Modul gibt die Möglichkeit der CallerID noch einen Präfix / Suffix hinzuzufügen, so dass die Zielperson sieht, dass der Anruf umgeleitet wurde.

## Abwurfplatz & Ausnahmen
Hier wird definiert, für welche Rufnummern, welcher Abwurfplatz verwendet werden soll.
Ebenso können bei der Ausnahme, wieder Ausnahme zu diesen Filtern definiert werden.

Mögliche Formate:
* 00491234567890 ==> Exakte Nummer
* 0049123456\* ==> Alle Nummern die mit 0049123456 beginnen
* \*789 ==> Alle Nummern die mit 789 Aufhören
* \*123\* ==> Alle Nummern die 123 irgendwo in der Nummer enthalten
*  12. ==> Alle dreistelligen Nummern, die mit 12 beginnen
* .23 ==> Alle dreistelligen Nummern, die mit 23 aufhören
* .2. ==> Alle dreistelligen Nummern, die mit einem Beliebigen Zeichen beginnen, eine zwei in der Mitte haben, und mit einem Beliebigen zeichen Aufhören.
* ... ==> Alle dreistelligen Nummern
* .23\* ==> Alle Zahlen, die mit einer Zahl beginnen, darauf mit 23 Folgen, und danach mit Beliebig vielen Zeichen aufhören 

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung


