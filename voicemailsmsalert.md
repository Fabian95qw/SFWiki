---
title: Voicemail SMS Alamierung
description: 
published: false
date: 2022-09-22T07:47:57.067Z
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

![targetmailbox.png](/uploads/voicemailsmsalert/targetmailbox.png)

## Zu überwachende Voicemailbox \*9
Es muss eine Zielvoicemailbox für das Modul gewählt werden.

> Es überwacht nur den "Neu" Tab, der "Privat" und "Alt" Tab werden nicht überwacht.
{.is-warning}

## Auszuführender User
Voicemailboxen können nur im Namen eines Benutzers abgerufen werden, das Modul versucht in Namen dieses Benutzers auf die Voicemailbox zuzugreifen.

## Prüfungsintervall
In diesem Intervall wird auf neue Voicemails geprüft, standardmässig wird die Voicemailbox alle 5 Minuten überprüft.

## Jetzt prüfen
Wenn das Modul übernommen/abgespeichert wird, wird automatisch auf neue Voicemails geprüft.

## Zeitplan
Hier kann ein Zeitplan gesetzt werden. Der Zeitraum basiert auf dem gleichen Prinzip, wie die Zeitgest. Umleitung der STARFACE: https://knowledge.starface.de/pages/viewpage.action?pageId=46566379
Das SMS Ziel muss als vollständig internationalisierte Nummer hinterlegt werden.

> Wenn sich Zeiträume überschneiden, wird immer nur das Ziel des ersten Zeitraums verwendet.
{.is-warning}

## Sprache von Datum/Uhrzeit
Das Format für den Zeitplan kann hier, geau gleich wie beim Zeitgest. Umleitungsmodul gesetzt werden.

## SMS-Dienst
Hier kann gewählt werden, über welchen SMS-Dienst die SMS Versendet wird, aktuell wird nur websms.com unterstützt.

## SMS-Text
Der SMS Text, welcher an die Nummer gesendet werden soll. Diese kann mit einer Handvonn spezieller Parameter befüllt werden.

### Spezielle Parameter

\#STARTTIME\# Das Startdatum/Uhrzeit der Voicemail gemäss Datumsformat
\#ID\# Die DB-ID dieser Voicemail
\#CALLEDNUMBER\# Die Nummer, welche Angerufen wurde
\#CALLERNUMBER\# Die Nummer des Anrufers
\#DURATION\# Die länge der Voicemail
\#MAILBOXID\# Die Nummer der Mailbox (ohne *9)
\#MAILBOXNAME\# Der Name der Mailbox

## Datumsformat
Für die Darstellung des Datums im SMS wird dieses Format verwendet.
Für die Konfigurationsmöglichkeiten siehe: https://docs.oracle.com/javase/7/docs/api/java/text/SimpleDateFormat.html

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung