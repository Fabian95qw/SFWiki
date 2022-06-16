---
title: Mail 2 Call - Meldungstexte
description: 
published: false
date: 2022-06-16T11:20:22.225Z
tags: 
editor: markdown
dateCreated: 2022-06-16T10:58:11.274Z
---

# Beschreibung
Dieses Module Ruft in Regelmässigen Abständen die E-Mails von einem IMAP Konto ab, und prüft diese auf den Absender & Betreff. Wenn der Absender oder der Betreff mit einr Liste übereinstimmt, wird ein Alarm mit einer von 10 Vordefinierten Meldetexten ausgelöst, und eine Reihe von Rufnummern nacheinander Angerufen, bis jemand den Alarm Annimmt.

# Konfiguration

![config.png](/uploads/mail2call/config.png)

## Auswertung Absender
Ermöglicht es basierend auf dem Absender eine Meldenummer zu definieren.

## Auswertung Betreff
Ermöglicht es Basierend auf dem Betreff eine Meldenummer zu definieren.

## Zu Alamierende Rufnummern
Die Teilnehmer werden in der Reihenfolge, wie sie in der Liste definiert sind angerufen.

## Tastendruck Timeout
Das Modul benötigt immer einen Tastendruck von der Angerufenen Person, bevor es den Alarm abspielt.

## Checkintervall
Wie oft die E-Mails vom Mailserver abgerufen werden.

# IMAP Mailserver

Die Mails werden von einem IMAP Server bezogen.

> Es werden immer nur die Ungelesenen E-Mails abgerufen, und diese werden dann ebenfalls als gelesen Markiert{.is-info}

![imap.png](/uploads/mail2call/imap.png)

# Audiodateien

Hier können die eigenen Audiodateien hinterlegt werden.

![audio.png](/uploads/mail2call/audio.png)

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung