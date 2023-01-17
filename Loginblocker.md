---
title: Loginblocker
description: 
published: true
date: 2023-01-17T15:38:51.348Z
tags: 
editor: markdown
dateCreated: 2023-01-17T14:50:02.779Z
---

# Beschreibung
Dieses Modul ermöglicht es, Benutzern die Anmeldung per UCI für bestimmte Endgerätetypen (Z.b. Android, IOS, Windows, Mac...) zu verhindern/erlauben.

# Hinweise

> Bei einem Systemneustart der STARFACE, gibt es ein kurzes Zeitfenster, in dem die Module noch nicht wieder aktiv sind, aber Benutzer sich bereits wieder an der Anlage anmelden können. In diesem Zeitfenster können sich auch Benutzer Anmelden, welche sonst blockiert wären. Dies lässt sich nicht verhindern.
{.is-danger}

> Bereits eingeloggte UCI-Clients können durch das Modul nicht ausgeloggt werden. Es wird lediglich das Abrufen von neuen Informationen unterdrückt, bereits Abgerufene Informationen stehen auf der App nach wie vor zur Verfügung.
{.is-warning}

> Der Zugriff auf das Webinterface wird durch dieses Modul nicht eingeschränkt.
{.is-info}

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

![Example1.PNG](/uploads/loginblocker/Example1.PNG)

Die Mitglieder der Gruppe "Zentrale" dürfen sich lediglich an der STARFACE App für Windows oder Mac anmelden. Alle anderen Benutzer der Anlage können einen beliebigen Client verwenden.

## Beispiel 2:

![Example2.PNG](/uploads/loginblocker/Example2.PNG)

Alle Benutzer der STARFACE mit ausnahme der Mitglieder der "Zentrale" können sich lediglich an der STARFACE App für Windows oder Mac anmelden.

## Beispiel 3:

![Example3.PNG](/uploads/loginblocker/Example3.PNG)

Das Modul hat keine Funktionalität, da keine Gruppe angegeben wurde, die Blockiert werden sollte.

## Beispiel 4:

![Example4.PNG](/uploads/loginblocker/Example4.PNG)

Alle Benutzer der STARFACE können sich lediglich an der STARFACE App für Windows oder Mac anmelden.

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung