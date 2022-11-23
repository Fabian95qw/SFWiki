---
title: Voicemail Alamierung
description: 
published: false
date: 2022-11-23T09:46:52.092Z
tags: 
editor: markdown
dateCreated: 2022-11-23T09:44:28.591Z
---

# Beschreibung

Dieses Modul überwacht eine spezifische Voicemailbox auf neue Voicemails.
Wenn eine neue Voicemail ankommt, werden mehrere Benutzer gemäss einer Eskalatiosnstufe nacheinander angerufen. 
Wenn ein Benutzer den Anruf annimmt, wird er aufgefordert eine DTMF Taste zu drücken. Anschliessend wird ihm das Voicemail abgespielt.
Sind alle Eskalationsstufen durch, und der Anruf wurde nicht zugestellt, so wird ein Alarm E-Mail verschickt.

# Konfiguration

![targetmailbox.png](/uploads/voicemailsmsalert/targetmailbox.png)

## Zu überwachende Voicemailbox \*9
Es muss eine Zielvoicemailbox für das Modul gewählt werden.

> Es überwacht nur den "Neu" Tab, der "Privat" und "Alt" Tab werden nicht überwacht.
{.is-warning}

## Auszuführender User
Voicemailboxen können nur im Namen eines Benutzers abgerufen werden, das Modul versucht in Namen dieses Benutzers auf die Voicemailbox zuzugreifen.

# Zeitplan & SMS Text

![timeplan.png](/uploads/voicemailsmsalert/timeplan.png)

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

# Alamierung bei Problemen

![alarmsettings.png](/uploads/voicemailsmsalert/alarmsettings.png)

# SMS-Dienst Zugangsdaten

## Websms
Bei Websms.com muss für das Versenden von SMS der Benutzername & das Passwort des Kontos hinterlegt werden.
![websms.com.png](/uploads/voicemailsmsalert/websms.com.png)

## Testmodus
Im Testmodus wird die API des SMS-Dienstes angesprochen, aber das effektive SMS nicht versendet.

# SMS-Log
Das Modul führt einen internen SMS-Log, dort werden alle bereits versendeten SMS angezeigt.
Das Modul nutzt diese Liste, um zu verhindern, dass für das gleiche Voicemail mehrere SMS versendet werden.

> Werden Einträge aus dieser Liste gelöscht, und das entsprechende Voicemail befindet sich noch im Tab "Neu" der Voicemailbox wird ein neues SMS für diese Voicemail generiert!
{.is-danger}

![sms-log.png](/uploads/voicemailsmsalert/sms-log.png)




# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung