---
title: CDR Export
description: 
published: true
date: 2024-02-20T13:45:09.570Z
tags: 
editor: markdown
dateCreated: 2024-02-20T13:18:54.502Z
---

# Beschreibung

Ermöglicht den CDR Export von Benutzern, Gruppen und IQueues auf SMB/FTP

# Konfiguration

![1.PNG](/uploads/cdr-export/1.PNG)

## Automatische Ausführung
Das Modul führt den Export in diesem Intervall aus

## Jetzt ausführen
Das Modul führt einen Export aus, wenn das Modul gespeichert / übernommen wird.
Dies ist für Testzwecke gedacht.

> Wenn das Modul übernommen wird, und nicht gespeichert, wir die Deltainformation nicht aktualisiert, dann kann es dazu kommen, dass die gleichen CDR's zweimal in zwei verschiedenen CSV-Dateien aufgelistet werden.
{.is-warning}

## CDR-Export für IQueue Gruppe
Generiert einen CDR-Report spezifisch mit den Spalten der IQueue Reports, anstatt den Standard CDR Exports.

## CDR-Export für Gruppe
Generiert einen CDR-Report für die Anrufe dieser Gruppe

## CDR-Export für Mitglieder der Gruppe
Generiert einen CDR-Report pro Benutzer in der Gruppe mit seinen individuellen CDR's.

## Variablen
Das Modul unterstützt einige Variablen, welche an verschiedenen Orten im Modul gesetzt werden können.

#DATE# -> Datum gemäss Formatierung
#FIRSTNAME# -> Vorname des Benutzers
#FAMILYNAME# -> Nachname des Benutzers
#GROUPNAME# -> Name der Gruppe
#LOGINID# -> LoginId des Benutzers/Gruppe (Je nach Exportoption)
#EMAIL# -> E-Mail Adresse des Benutzer

## CSV-Dateiname
Der Dateiname der Exportierten CSV Datei. Unterstützt Variablen.

## Formatierung der Datumsvariable #DATE#
In welchem Format die Datumsvariable sein soll, gemäss [SimpleDateFormat](https://docs.oracle.com/javase/7/docs/api/java/text/SimpleDateFormat.html)

# Transfer
Hier wird definiert, ob die Datei per SMB oder FTP übertragen werden soll.

![2.PNG](/uploads/cdr-export/2.PNG)

## Variablenunterstüzung
Hier können die Variablen beim SMB-Unterverzeichnis sowie FTP-Unterverzeichnis verwendet werden.


# Experteneinstellungen

> Diese Werte dürfen nicht angepasst werden, ausser es wurde so durch die SI-Solutions GmbH beauftragt
{.is-danger}

![3.PNG](/uploads/cdr-export/3.PNG)

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung