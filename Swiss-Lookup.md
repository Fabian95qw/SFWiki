---
title: Swiss-Lookup
description: 
published: true
date: 2023-01-02T14:40:30.133Z
tags: 
editor: markdown
dateCreated: 2023-01-02T14:18:05.809Z
---

# Beschreibung
Dieses Modul macht einen Lookup gegen Schweizer Telefonbücher. Aktuell wird nur das Tel.Search.ch (Swissdirectories) unterstützt, es ist noch die Unterstützung für weitere Telefonbücher geplant.

Das Modul hat eine interne Datenbank, in denen bereits aufgerufene Einträge gespeichert werden können, damit sie nicht wiederholt bei den Telefonbuchanbietern abgefragt werden, da es dort Limitierungen zu den Anzahl anfragen pro Stunde/Tag/Monat gibt.

# Konfiguration

![1.png](/uploads/swiss-lookup/1.png)

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

# Tel.Search<span></span>.ch Einstellungen

![2.png](/uploads/swiss-lookup/2.png)

## API-Key
Hier wird der von der Tel.search<span></span>.ch zur Verfügung gestellte API Key benötigt.
Einen API-Key kann man unter: https://tel.search.ch/api/getkey.en.html anfordern.

## Sprache der Ausgabe
Tel.search.<span></span>ch kann die Suchergebnisse in allen Landessprachen + Englisch liefern. Hier kann definiert werden, welche davon für die Suchergebnisse verwendet wird.

## Formatierung CallerID
Wenn der Anruf durch die Tel.Search.<span></span>ch aufgelöst wird, wir die CallerID entsprechend Formatiert. Hier können alle unter von Tel.Search.ch unter dem Link: https://tel.search.ch/api/help.en.html unter "Format of Response" angegebene Parameter verwendet werden.

> Die CallerID wird in diesem Format in die DB gespeichert. Nachträgliche Änderungen haben keine Einfluss auf bereits abgespeicherte Einträge. 
{.is-warning}

## Maximale Zeichenlänge der Werte
Für alle Werte, welche in der CallerID verwendet werden, muss jeweils die Maximale Zeichenlänge hinterlegt werden. Bei einer länge von 0 wird dieser nicht gekürzt.

### Beispiel:
CallerID Format: #name# #firstname# #org#

| Wert | Maximale Zeichenlänge|
|---|---|
| name | 6 |
| firstname | 0 |
| company | 10 |

Der Anrufer ist "Max Mustermann Musterfirma".
Der Vorname Max, wird nicht gekürzt, der Nachname wird auf 6 Zeichen "Muster" gekürzt, und der Firmenname auf "Musterfirm" gekürtzt. das Ergebnis wäre "Max Muster Musterfirm"

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung