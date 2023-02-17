---
title: Quelle: SQL-Datenbanken
description: 
published: true
date: 2023-02-17T09:09:21.450Z
tags: 
editor: markdown
dateCreated: 2023-02-17T08:57:39.954Z
---

# Beschreibung

Hier geht es spezifisch um die Konfiguration des SQL-Connectors im Adressbuch Importer

# Konfiguration

![sql-config.png](/uploads/adressbuch-importer-sql/sql-config.png)

## Datenbanktyp
Hier wird definiert, was für ein Datenbank Typ verwendet werden soll.

Aktuell werden Folgende unterstützt:

- PostgreSQL
- Derby
- MSSQL
- MySQL
- MariaDB

Falls sie einen anderen Datenbanktyp benötigen, kontaktieren sie uns bitte per E-Mail

## IP / Port / Login / Passwort
Die Verbindungsdaten für die Datenbank.

## Zusätzliche Parameter
Gewisse Datenbanken können Optionale/Zusätzliche Parameter annehmen, diese können hier im Format \[Name\]=\[Wert\]&\[Name\]=\[Wert\]... hinterlegt werden.

## SQL-Query
Hier muss eine komplette SQL-Query als .txt Datei hochgeladen werden.
Z.b. SELECT * FROM account;

## Header Template
Damit das Modul weiss, welche Spalte aus der Datenbank, welchem Feld in der STARFACE zugewiesen werde muss, muss ein entsprechendes Template erzeugt werden.

### Beispiel Template

**Beispieldaten aus Applikation XY**

![Vorlageappxy](/uploads/adressbuch-importer/vorlageappxy.png "Vorlageappxy")

Diese sollen in die Starface Importiert werden. Hierfür kann ein Template generiert werden.
Als Vorlage für das Template benutzen wir die CSV-Import Vorlage der Starface:

![Template](/uploads/adressbuch-importer/template.png "Template")

Die darin enthaltenen Spaltennamen werden von der Starface erkannt.

Wir platzieren nun die Header in den Spalten, die den entsprechenden Spalten in der SQL-DB Entsprechen:

![Vorlageresult](/uploads/adressbuch-importer/vorlageresult.png "Vorlageresult")

**Das Resultierende Template muss im CSV Format Semicolon ( ; ) getrennt & im UTF-8 Format abgespeichert werden.**

In diesem Fall würde der „rohe“ CSV-Code so aussehen:

> [LEER];Name [contact:familyname];Vorname [contact:firstname];;Firma [contact:company];PLZ [address:postcode];Straße [address:street];;Rufnummer [telephone:phone]


# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung
