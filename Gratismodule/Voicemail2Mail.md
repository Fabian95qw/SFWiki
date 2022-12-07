---
title: Voicemail als E-Mail
description: 
published: true
date: 2022-12-07T08:52:38.104Z
tags: 
editor: markdown
dateCreated: 2022-12-07T08:49:03.552Z
---

# Beschreibung

Dieses Modul überwacht eine spezifische Voicemailbox auf neue Voicemails.
Wenn eine neue Voicemail ankommt, wird eine E-Mail versendet.

Dies ist gedacht um bei Gruppen-Voicemails eine spezifische E-Mail Adresse hinterlegen zu können.


# Konfiguration

![1](/uploads/voicemail2mail/1.png)

## Jetzt Ausführen
Prüft beim Speichern die Voicemailbox auf neue Nachrichten, und löst ggf. den ganzen Prozess aus.

## Zu überwachende Voicemailbox *9
Es muss eine Zielvoicemailbox für das Modul gewählt werden.
> Es überwacht nur den "Neu" Tab, der "Privat" und "Alt" Tab werden nicht überwacht.
{.is-warning}

## Auszuführender User
Voicemailboxen können nur im Namen eines Benutzers abgerufen werden, das Modul versucht in Namen dieses Benutzers auf die Voicemailbox zuzugreifen.

## Prüfungsintervall
In diesem Intervall wird auf neue Voicemails geprüft, standardmässig wird die Voicemailbox alle 5 Minuten überprüft.

## Ziel E-Mail Adresse:
Die Voicemail E-Mail wird an diese Adresse versendet.

## E-Mail Formatierungsmöglichkeiten
Der E-Mail Betreff & Text kann mit div. Parametern befüllt werden:

#DATE# ==> Datum im Format: \[dd.MM.yyyy HH:mm\]
#CALLERNUMBER# ==> Nummer des Anrufers
#CALLERNAME# ==> Name des Anrufers (Falls auflösbar)
#CALLEDNUMBER# ==> Angerufene Nummer
#ID# ==> ID dieser Voicemail
#MAILBOXID# ==> ID der Voicemailbox
#MAILBOXNAME# ==> Name der Voicemailbox

## E-Mail Absender
Der Absendername, welcher angezeigt werden soll

## E-Mail Betreff
Betreff des E-Mails mit entsprechenden Parametern.
Standard: **Neue Voicemail #ID# \[#DATE#\]**

## E-Mail Text
Text des E-Mails mit entsprechenden Parametern.
Standard: **\[#DATE#\] Neue Voicemail von #CALLERNUMBER# #CALLERNAME#**

## Voicemail Anhängen
Hängt die .wav Datei des Voicemails direkt am E-Mail an.

# Voicemaillog
Alle ausgeführten Voicemails werden im Modul Voicemaillog Dokumentiert.

> Das löschen von Zeilen führt dazu, dass diese Voicemail als neu angesehen wird, und das Modul führt den Alarm für diese spezifische Voicemail erneut aus, sofern diese sich noch im Tab "Neu" befindet!
{.is-danger}

![2](/uploads/voicemail2mail/2.png)

## Voicemailid
Die Datenbank Voicemail ID, um welche es sich handelt.

## Ergebnis
Es gibt aktuell zwei Ergebnisse:
\[dd.MM.yyyy HH:mm\] E-Mail Erfolgreich! | Anrufer:  #CALLERNUMER# | Angerufen: #CALLEDNUMBER#
\[dd.MM.yyyy HH:mm\] E-Mail Fehlgeschlagen!  | Anrufer:  #CALLERNUMER# | Angerufen: #CALLEDNUMBER#

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung