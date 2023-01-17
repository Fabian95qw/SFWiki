---
title: Loginblocker
description: 
published: false
date: 2023-01-17T15:24:44.602Z
tags: 
editor: markdown
dateCreated: 2023-01-17T14:50:02.779Z
---

# Beschreibung
Dieses Modul ermöglicht es, Benutzern die Anmeldung per UCI für bestimmte Endgerätetypen (Z.b. Android, IOS, Windows, Mac...) zu verhindern/erlauben.

# Hinweis
> Bereits eingeloggte Mobile-Clients können durch das Modul nicht ausgeloggt werden.
{.is-danger}

> Bei einem Systemneustart der STARFACE, gibt es ein kurzes Zeitfenster, in dem die Module noch nicht wieder aktiv sind, aber Benutzer sich bereits wieder an der Anlage anmelden können. In diesem Zeitfenster können sich auch Mobilbenutzer Anmelden, welche sonst blockiert wären. Dies lässt sich nicht verhindern.
{.is-danger}

# Flow
![Flow.jpg](/uploads/loginblocker/Flow.jpg)

# Konfiguration

![1.png](/uploads/loginblocker/1.png)

## Gruppenmodus
Definiert, ob nur die Mitglieder der Gruppe überwacht werden sollen (Blacklist), oder alle, ausser die Mitglieder in der Gruppe (Whitelist)

## Gruppe
Die Gruppe, welche Überwacht werden soll

## Erlaubte Clients
Welche Clients für die Überwachte Gruppe Zugelassen werden sollen.

> Gross Kleinschreibung muss korrekt sein.
{.is-warning}

- StarfaceWindows
- StarfaceMac
- Android
- IOS

# Beispiele

## Beispiel 1:


## Beispiel 2:

## Beispiel 3:

## Beispiel 4:

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung