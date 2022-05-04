---
title: PDF-Toolbox für STARFACE
description: 
published: false
date: 2022-05-04T08:23:52.920Z
tags: 
editor: markdown
dateCreated: 2022-05-04T07:40:20.498Z
---

# Beschreibung
Die PDF-Toolbox liefert eine vielzahl von Funktionen für das erstellen/editieren von PDF's:

- Neue PDF's erzeugen
- Existierende PDF's laden, und editieren (Ausser diese sind geschützt)
- Neue Seiten zu PDF's hinzufügen
- Neue Textelemente, Bilder, und editierbare Textzellen zu PDF's hinzufügen
- Vollständige Tabellen mit eigenem Tabellen-/Spalten-/Reihen-/Zellen-design erzeugen und in den PDF's hinterlegen
- Bestehende PDF-Formulare ausfüllen
- PDF-Dateien zusammenführen

# Quellcode:
Den Quellcode findet man unter: https://github.com/Fabian95qw/SF-Modulefunctions/tree/master/src/libraries/pdftoolbox/si/module/pdftoolbox
Vorkompillierte .class Dateien findet man unter: https://github.com/Fabian95qw/SF-Modulefunctions/tree/master/bin/libraries/pdftoolbox

# Beispielmodul
Ein Beispielmodul zur Anwendung der Modulbausteine findet ihr hier: https://github.com/Fabian95qw/SF-Modulefunctions/tree/master/bin/libraries/pdftoolbox

# Funktionen

## \[PDF\]Create PDF

<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
  ### Outputvariablen:
  PDF (OBJECT) Repräsentiert ein leeres PDF, welches sich im Arbeitsspeicher befindet. Dieses Objekt wird am schluss benötigt, umd es auf die Festplatte zu schreiben.
   
</details>

## \[PDF\]Loading Existing PDF

<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
### Inputvariablen:
Sourcefile (STRING): Der Absolute Pfad, zum PDF, welches fürs editieren geladen werden soll
  
>  PDF's welche einen Schreibschutz haben können nicht editiert werden  {.is-warning}

### Outputvariablen:
PDF (OBJECT) Repräsentiert das geladene PDF welches sich im Arbeitsspeicher befindet. Dieses Objekt wird am schluss benötigt, umd die Änderungen am PDF wieder auf die Festplatte zu schreiben-
     
</details>

## \[PDF\] Create new Page
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
### Inputvariablen:
PageSize (LEGAL ,LETTER ,A0 ,A1 ,A2 ,A3 ,A4 ,A5 ,A6), die grösse der neu zu erzeugenden Seite

### Outputvariablen:
Page (OBJECT): Repräsentiert eine leeres Seite, welches sich im Arbeitsspeicher befindet. **Diese Seite muss einem PDF Zugewiesen werden, damit diese im entsprechenden PDF abgespeichert wird.**

</details>

## \[PDF\] Get Page of an existing PDF
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
### Inputvariablen:
  PDF (OBJECT) Repräsentiert das geladene PDF welches sich im Arbeitsspeicher befindet.
  PageNumber (NUMBER): Die Seitennummer, welche extrahiert werden soll
  
### Outputvariablen:
Page (OBJECT): Repräsentiert die entsprechende Seite vom PDF. **Diese Seite muss dem PDF nicht erneut zugewiesen werden, damit sie abgespeichert wird.**

</details>

## \[PDF\]
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
### Inputvariablen:

### Outputvariablen:

</details>

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung


