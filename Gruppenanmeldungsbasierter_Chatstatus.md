---
title: Gruppenanmeldungsbasierter Chatstatus
description: 
published: true
date: 2021-11-16T09:58:46.519Z
tags: 
editor: markdown
dateCreated: 2021-11-16T09:30:00.294Z
---

# Beschreibung
Ein Modul, welches bei Usern basierend auf deren Mitgliedschaft in einer Gruppe einen Chatstatus, sowie Statustext setzt. Optional kann der Benutzer noch aus einer Gruppe ausgeloggt werden.

# Konfiguration

![1.png](/uploads/gruppenanmeldungsbasierter-chatstatus/1.png)

## Dienst
Das Modul benötigt einen Hintergrunddienst. Diese muss aber für Updates gestoppt werden, da sich sonst die Events Duplizieren. Für den Normalbetrieb muss der Dienst auf "Starten" stehen.

## Zu Überwachende Gruppe
Das Modul überwacht die Mitgliedschaft in dieser Gruppe. Es wird nur auf Mitglieder reagiert, welche Aktiv in dieser Gruppe sind.

## Zu setzender Status
Der Chatstatus der gesetzt werden soll. Möglich ist: Verfügbar, Abwesend, Bitte nicht stören, Abgemeldet.

## Zu setzender Statustext
Der Statustext, der gesetzt werden soll.

## Abzumeldende Gruppe
Die Gruppe aus der der Benutzer abgemeldet werden soll.
> Das Modul meldet teilnehmer nicht mehr an. Dies muss manuell getan werden.
{.is-danger}

# Beispiel

![2.gif](/uploads/gruppenanmeldungsbasierter-chatstatus/2.gif)

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung