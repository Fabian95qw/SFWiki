---
title: Voicemail SMS Alamierung
description: 
published: false
date: 2022-09-22T07:41:23.213Z
tags: 
editor: markdown
dateCreated: 2022-09-22T07:28:36.859Z
---

# Beschreibung

Dieses Modul überwacht eine spezifische Voicemailbox auf neue Voicemails.
Das Modul enthält eine Zeitplanung, mit verschiedenen Nummernzielen.
Wenn eine Voicemail eintrifft, wird der auf der Zeitplanung basierten Nummer eine SMS mit frei definierbarem Text via dem websms.com Dienst gesendet.
Trifft kein Zeitraum zu, so kann ein Alarm E-Mail generiert werden.

# Konfiguration

## Zu überwachende Voicemailbox \*9

## Auszuführender User

## Prüfungsintervall

## Jetzt prüfen

## Zeitplan
https://knowledge.starface.de/pages/viewpage.action?pageId=46566379

## Sprache von Datum/Uhrzeit

## SMS-Dienst

## SMS-Text

### Spezielle Parameter

\#STARTTIME\# Das Startdatum/Uhrzeit der Voicemail gemäss Datumsformat
\#ID\# Die DB-ID dieser Voicemail
\#CALLEDNUMBER\# Die Nummer, welche Angerufen wurde
\#CALLERNUMBER\# Die Nummer des Anrufers
\#DURATION\# Die länge der Voicemail
\#MAILBOXID\# Die Nummer der Mailbox (ohne *9)
\#MAILBOXNAME\# Der Name der Mailbox

## Datumsformat
Für die Darstellung des Datums wird dieses Format verwendet.
Für die spezifischen Konfigurationsmöglichkeiten siehe: https://docs.oracle.com/javase/7/docs/api/java/text/SimpleDateFormat.html

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung