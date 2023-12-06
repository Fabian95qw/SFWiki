---
title: Ansage in laufendem Gespräch
description: 
published: false
date: 2023-12-06T08:04:05.292Z
tags: 
editor: markdown
dateCreated: 2023-12-06T07:36:06.607Z
---

# Beschreibung
Das Modul soll für eine Gruppe von Benutzern sich in die Laufenden Gespräche einhängen, und dort in einem durch den Kunden setzbaren Intervall .wav Audiodateien abspielen.
Die Mitarbeiter sollen somit ein Zeitegefühl bekommen, wie lange sie bereits am Telefon und ggf. das Gespräch beenden.

Das Modul spielt diese Information nur auf den Audiokanälen von internen Teilnehmern ab.

> Anrufe, die von diesem Modul beobachtet werden können nicht mithilfe von ChanSpy/ModCall abgehört werden.
{.is-warning}

# Zweiteiliges Modul
Dieses Modul besteht aus zwei teilen, und es müssen zwei separate Module installiert werden.

# Konfiguration - Ansage in laufendem Gespräch - Kern

![1.PNG](/uploads/active_call_announcement/1.PNG)

## Rufnummer
Dem Modul muss eine Rufnummer zugewiesen werden, diese muss später im Manager Modul hinterlegt werden.

## Zu beobachtende Gruppe
Das Modul hängt sich nur in Anrufe von Mitgliedern dieser Gruppe ein.

## Ansage 
Im Modul können 4 separate Audiodateien hinterlegt werden, welche nacheinander abgepsielt werden.

## Zeit zwischen Ansagen
Zwischen den verschiedenen Ansagen können verschiedene Intervalle eingestellt werden.

# Konfiguration - Ansage in laufendem Gespräch - Manager

## Telefonnummer der Instanz

![2.PNG](/uploads/active_call_announcement/2.PNG)

Im zweiten Modul muss die Rufnummer des Kernmoduls hinterlegt werden. 
Mehr muss nicht konfiguriert werden.

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung