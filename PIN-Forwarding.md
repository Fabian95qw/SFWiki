---
title: PIN-Forwarding
description: 
published: false
date: 2024-04-26T08:04:24.318Z
tags: 
editor: markdown
dateCreated: 2024-04-26T08:00:04.375Z
---

# Beschreibung
Das Modul liest in regelmässigen Abständen eine .CSV Datei mit PIN-Forwarding Regeln ein.
Die PIN-Forwarding Regel besteht aus zwei Teilen, einem PIN, und einer Zielnummer.
Wenn das Modul angerufen wird, so soll ein Text abgespielt werden, dass den Anrufer zur PIN-Eingabe auffordert.
Der Anrufer gibt dann einen PIN mit \[n\] stellen per DTMF-interaktion ein.
Das Modul prüft, ob dieser PIN in der zuvor eingelesenen CSV exisitert.
Wenn der PIN exisitert, wird der Anrufer zur dahinterliegenden Nummer weitergeleitet.
Wenn der PIN nicht exisitert, oder der Anrufer keinen Vollständigen PIN in \[n\] Sekunden eingibt, soll der Anruf an eine Failover Nummer weitergeleitet werden.

# Konfiguration



# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung