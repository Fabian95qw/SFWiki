---
title: Swiss-Lookup
description: 
published: true
date: 2023-01-02T14:18:05.809Z
tags: 
editor: markdown
dateCreated: 2023-01-02T14:18:05.809Z
---

# Beschreibung
Dieses Modul macht einen Lookup gegen Schweizer Telefonbücher. Aktuell wird nur das Tel.Search.ch (Swissdirectories) unterstützt, es ist noch die Unterstützung für weitere Telefonbücher geplant.

Das Modul hat eine interne Datenbank, in denen bereits aufgerufene Einträge gespeichert werden können, damit sie nicht wiederholt bei den Telefonbuchanbietern abgefragt werden, da es dort Limitierungen zu den Anzahl anfragen pro Stunde/Tag/Monat gibt.

# Konfiguration

## Lookup Timeout \[s\]
Definiert wie viel Zeit das Modul maximal aufwenden darf, um die Rufnummer gegen externe Telefonbücher aufzulösen. Sollte der Timeout erreicht werden, so wird der Anruf unaufgelöst weitergegeben.

## Aufgelöste Adressen in interner DB Speichern.
Sofern aktiviert, wird die Vollständige internationalisierte Rufnummer in einer internen DB abgespeichert.

## Interne DB - Funktionen
Man kann entweder eine Rufnummer gegen die interne DB Abfragen, oder diese aus der internen DB löschen. Dies wird z.b. benötigt, wenn die CallerID geändert wurde, oder die interne Beschriftung generell nicht mehr stimmt.

## Suchbegriff
Hier muss die Rufnummer ohne leerzeichen Vollständig internationalisiert eingetippt werden.

## Sucheregebnis
Hier wird entweder die in der internen DB abgelegte CallerID angezeigt, oder es kommt eine Meldung, dass dieser nicht gefunden wurde.

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung