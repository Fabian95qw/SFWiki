---
title: PDF-Toolbox für STARFACE
description: 
published: false
date: 2022-05-04T08:53:18.455Z
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

# Offset's
Bei der Erzeugung des PDF's wird immer mit Offsets, anstatt mit absoluten Positionswerten gearbeitet.
Der Offset X:0 und Y:0 repräsentiert immer den unteren Linken Ecke der Seite.

Beispiel mit einem Bild:
Offset X: 50
Offset Y: 750

<details>
  <summary>Bild (Klicken zum Anzeigen)</summary>
	
![Offset.PNG](/uploads/pdftoolbox/Offset.PNG)
   
</details>


# Funktionen

## \[PDF\]Create PDF
Ein neues leeres PDF erzeugen
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
  ### Outputvariablen:
  PDF (OBJECT) Repräsentiert ein leeres PDF, welches sich im Arbeitsspeicher befindet. Dieses Objekt wird am schluss benötigt, umd es auf die Festplatte zu schreiben.
   
</details>

## \[PDF\]Loading Existing PDF
Ein bestehendes PDF laden
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
### Inputvariablen:
Sourcefile (STRING): Der Absolute Pfad, zum PDF, welches fürs editieren geladen werden soll
  
>  PDF's welche einen Schreibschutz haben können nicht editiert werden  {.is-warning}

### Outputvariablen:
PDF (OBJECT) Repräsentiert das geladene PDF welches sich im Arbeitsspeicher befindet. Dieses Objekt wird am schluss benötigt, umd die Änderungen am PDF wieder auf die Festplatte zu schreiben-
     
</details>

## \[PDF\] Create new Page
Eine neue leere Seite erzeugen
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>

### Inputvariablen:
PageSize (LEGAL ,LETTER ,A0 ,A1 ,A2 ,A3 ,A4 ,A5 ,A6), die grösse der neu zu erzeugenden Seite

### Outputvariablen:
Page (OBJECT): Repräsentiert eine leeres Seite, welches sich im Arbeitsspeicher befindet. **Diese Seite muss einem PDF Zugewiesen werden, damit diese im entsprechenden PDF abgespeichert wird.**

</details>

## \[PDF\] Get Page of an existing PDF
Eine PDF Seite von einem existierenden PDF Abrufen
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
### Inputvariablen:
  PDF (OBJECT) Repräsentiert das geladene PDF welches sich im Arbeitsspeicher befindet.
  PageNumber (NUMBER): Die Seitennummer, welche extrahiert werden soll
  
### Outputvariablen:
Page (OBJECT): Repräsentiert die entsprechende Seite vom PDF. **Diese Seite muss dem PDF nicht erneut zugewiesen werden, damit sie abgespeichert wird.**

</details>

## \[PDF\]Add Image to Page
Ein Bild auf einer Seite einfügen
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
### Inputvariablen:
  PDF (OBJECT) Das PDF, zu dem das Bild hinzugefügt werden soll.
  Page (OBJECT): Die Seite in diesem PDF, zu dem das Bild hinzugefügt werden soll.
  Path to Image (STRING): Der Pfad zum Bild, welches eingefügt werden soll.
  Width (NUMBER): Das Bild wird auf diese Länge Skaliert. Wenn 0 gesetzt wird, bleibt es auf Originalgrösse
  Height (NUMBER): Das Bild wird auf diese Höhe Skaliert. Wenn 0 gesetzt wird, bleibt es auf Originalgrösse
  Offset X (NUMBER): Offset in Breite
  Offset Y (NUMBER): Offset in Höhe
  
</details>

## \[PDF\]Add Text to Page
Reiner Text auf einer Seite einfügen
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
### Inputvariablen:
  PDF (OBJECT) Das PDF, zu dem das Bild hinzugefügt werden soll.
  Page (OBJECT): Die Seite in diesem PDF, zu dem das Bild hinzugefügt werden soll.
  Text (STRING): Der Text, welcher dort Platziert werden soll
  Font (DEFAULT, HELVETICA, HELVETICA_BOLD, HELVETICA_BOLD_OBLIQUE, HELVETICA_OBLIQUE, COURIER, COURIER_BOLD, COURIER_BOLD_OBLIQUE, COURIER_OBLIQUE, SYMBOL, TIMES_BOLD, TIMES_BOLD_ITALIC, TIMES_ITALIC, TIMES_ROMAN, ZAPF_DINGBATS): Die Schriftart
  Font Size (NUMBER): Schriftgrösse [pt]
  Offset X (NUMBER): Offset in Breite
  Offset Y (NUMBER): Offset in Höhe
  
</details>

## \[PDF\]Add Textfield to Page
Ein Textfeld, welches ausgefüllt werden kann auf einer Seite einfügen
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
### Inputvariablen:
  PDF (OBJECT) Das PDF, zu dem das Bild hinzugefügt werden soll.
  Page (OBJECT): Die Seite in diesem PDF, zu dem das Bild hinzugefügt werden soll.
  Fieldname (STRING): Der Name des Formularfelds. Dies wird bei der Auswertung von Formularen benötigt.
  Text (STRING): Der Text, der Vorbefüllt werden soll
  Width (NUMBER): Das Textfeld wird auf diese Länge skaliert. 
  Height (NUMBER): Das Textfeld wird auf diese Höhe skaliert.
  Offset X (NUMBER): Offset in Breite
  Offset Y (NUMBER): Offset in Höhe
  Bordercolor (R,G,B): Die Farbe des Feldrandes im Format [R,G,B] Z.b. 255,128,64
  Backgroundcolor: Die Farbe des Hintergrunds (Bei aktiver selektion)im Format [R,G,B] Z.b. 255,128,64
  Allow Editing of Textfield: Ob der Inhalt dieses Textfeldes editiert werden darf.
  
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


