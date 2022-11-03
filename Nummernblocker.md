---
title: Nummernblocker
description: 
published: true
date: 2022-11-03T13:04:22.320Z
tags: 
editor: markdown
dateCreated: 2022-11-03T12:43:15.139Z
---

# Beschreibung

Das Modul erlaubt einzuschränken, wohin Gruppen von Benutzern Telefonieren/Nicht Telefonieren dürfen.

# Konfiguration

![1.png](/uploads/numberblocker/1.png)

## Zu Überwachende Gruppe
Das Modul überwacht nur Mitglieder dieser Gruppe.

## Modus
Im Blacklist Modus werden nur diese spezifsichen Nummern Blockiert.
Im Whitelsit Modus werden alle ausser den spezifizierten Nummern Blockiert.

> Wenn der Modus auf Whitelist steht, und kein Eintrag in der Liste ist, können Gruppenmitglieder generell nicht Telefonieren.
{.is-warning}

## Nummernfilter
Erlaubt es Nummern zu filtern.
Beispiele:
\+41\*:Nur Nummern die mit +41 Beginnen
2\?\?:Nur Nummern die, welche mit einer 2 Beginnen, und zwei weitere Zahlen enthalten.
\?\?\?: Nur 3 Stellige Nummern
004112345678:Nur die Nummer 004112345678
\+49\*80: Nur +49 er Nummer, die mit 80 aufhören 

## Ansage bei Verstoss
Wenn jemand gegen den Filter verstösst, kann ihm eine Ansage abgespielt werden. Ansonsten kommt bei Verstössen ein Besetztton.

## Verstösse Melden
Die Verstösse können an eine oder mehrere E-Mail Adressen gesendet werden.
Die Vertoss E-Mails enthalten den Folgenden Text:

Der interne Benutzer: \[Benutzername\] \[Interne Rufnummer des Benutzers\]  hat Versucht die Nummer \[Zielnummer\] anzurufen.


# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung