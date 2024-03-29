---
title: PDF-Toolbox für STARFACE
description: 
published: true
date: 2022-05-09T10:00:37.988Z
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
- PDF (OBJECT) Repräsentiert ein leeres PDF, welches sich im Arbeitsspeicher befindet. Dieses Objekt wird am schluss benötigt, umd es auf die Festplatte zu schreiben.
   
</details>

## \[PDF\]Loading Existing PDF
Ein bestehendes PDF laden
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
### Inputvariablen:
- Sourcefile (STRING): Der Absolute Pfad, zum PDF, welches fürs editieren geladen werden soll
  
>  PDF's welche einen Schreibschutz haben können nicht editiert werden  {.is-warning}

### Outputvariablen:
- PDF (OBJECT) Repräsentiert das geladene PDF welches sich im Arbeitsspeicher befindet. Dieses Objekt wird am schluss benötigt, umd die Änderungen am PDF wieder auf die Festplatte zu schreiben-
     
</details>

## \[PDF\] Create new Page
Eine neue leere Seite erzeugen
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>

### Inputvariablen:
- PageSize (LEGAL ,LETTER ,A0 ,A1 ,A2 ,A3 ,A4 ,A5 ,A6), die grösse der neu zu erzeugenden Seite

### Outputvariablen:
- Page (OBJECT): Repräsentiert eine leeres Seite, welches sich im Arbeitsspeicher befindet. **Diese Seite muss einem PDF Zugewiesen werden, damit diese im entsprechenden PDF abgespeichert wird.**

</details>

## \[PDF\] Get Page of an existing PDF
Eine PDF Seite von einem existierenden PDF Abrufen
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
### Inputvariablen:
- PDF (OBJECT) Repräsentiert das geladene PDF welches sich im Arbeitsspeicher befindet.
- PageNumber (NUMBER): Die Seitennummer, welche extrahiert werden soll
  
### Outputvariablen:
- Page (OBJECT): Repräsentiert die entsprechende Seite vom PDF. **Diese Seite muss dem PDF nicht erneut zugewiesen werden, damit sie abgespeichert wird.**

</details>

## \[PDF\]Add Image to Page
Ein Bild auf einer Seite einfügen
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
### Inputvariablen:
- PDF (OBJECT) Das PDF, zu dem das Bild hinzugefügt werden soll.
- Page (OBJECT): Die Seite in diesem PDF, zu dem das Bild hinzugefügt werden soll.
- Path to Image (STRING): Der Pfad zum Bild, welches eingefügt werden soll.
- Width (NUMBER): Das Bild wird auf diese Länge Skaliert. Wenn 0 gesetzt wird, bleibt es auf Originalgrösse
- Height (NUMBER): Das Bild wird auf diese Höhe Skaliert. Wenn 0 gesetzt wird, bleibt es auf Originalgrösse
- Offset X (NUMBER): Offset in Breite
- Offset Y (NUMBER): Offset in Höhe
  
</details>

## \[PDF\]Add Text to Page
Reiner Text auf einer Seite einfügen
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
### Inputvariablen:
- PDF (OBJECT) Das PDF, zu dem das Bild hinzugefügt werden soll.
- Page (OBJECT): Die Seite in diesem PDF, zu dem das Bild hinzugefügt werden soll.
- Text (STRING): Der Text, welcher dort Platziert werden soll
- Font (DEFAULT, HELVETICA, HELVETICA_BOLD, HELVETICA_BOLD_OBLIQUE, HELVETICA_OBLIQUE, COURIER, COURIER_BOLD, COURIER_BOLD_OBLIQUE, COURIER_OBLIQUE, SYMBOL, TIMES_BOLD, TIMES_BOLD_ITALIC, TIMES_ITALIC, TIMES_ROMAN, ZAPF_DINGBATS): Die Schriftart
- Font Size (NUMBER): Schriftgrösse [pt]
- Font Color (R,G,B): Die Farbe des Textes im Format [R,G,B] Z.b. 255,128,64
- Offset X (NUMBER): Offset in Breite
- Offset Y (NUMBER): Offset in Höhe
  
</details>

## \[PDF\]Add Textfield to Page
Ein Textfeld, welches ausgefüllt werden kann auf einer Seite einfügen
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
### Inputvariablen:
-   PDF (OBJECT) Das PDF, zu dem das Bild hinzugefügt werden soll.
-   Page (OBJECT): Die Seite in diesem PDF, zu dem das Bild hinzugefügt werden soll.
-   Fieldname (STRING): Der Name des Formularfelds. Dies wird bei der Auswertung von Formularen benötigt.
-   Text (STRING): Der Text, der Vorbefüllt werden soll
-   Width (NUMBER): Das Textfeld wird auf diese Länge skaliert. 
-   Height (NUMBER): Das Textfeld wird auf diese Höhe skaliert.
-   Offset X (NUMBER): Offset in Breite
-   Offset Y (NUMBER): Offset in Höhe
-   Bordercolor (R,G,B): Die Farbe des Feldrandes im Format [R,G,B] Z.b. 255,128,64
-   Backgroundcolor: Die Farbe des Hintergrunds (Bei aktiver selektion)im Format [R,G,B] Z.b. 255,128,64
-   Allow Editing of Textfield: Ob der Inhalt dieses Textfeldes editiert werden darf.
  
</details>

## \[PDF\] Fill out an existing PDF Form
Füllt das Formular eines bestehenden PDF's aus, und Speichert es in einer neuen Datei ab
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
### Inputvariablen:

- Template (STRING): Das Originale Formular/die Vorlage, die Befüllt werden soll.
- Targetfile (STRING): Wo die Ausgefüllte Version abgespeichert werden soll.
- Mapping (MAP) Map<Fieldname, Content> Setzt den Inhalt eines Felds basierend auf dem Felnamen. Z.b:"Textbox1', '7.2.0.1'} setzt den Inhalt der "Textbox1" auf den Wert "7.2.0.1"
- Replacement (MAP) Map<Searchstring, Replacementstring>.Ersetzt den Inhalt eines Feldes basierend auf dem Suchbegriff. Z.b. {'%SFVersion%'. '7.2.0.1'} Prüft alle Felder auf den Wert "%SFVersion%" und ersetzt alle gefundenen Instanzen davon mit "7.2.0.1".
- Beispiel: Feld beinhaltet: "STARFACE-Version:%SFVersion%" Ergebnis: "STARFACE-Version:7.2.0.1"
- SetReadOnly (BOOLEAN) Sets edited Fields to readonly, so they can't be edited by hand later on
</details>

## \[PDF\] Merge Multiple PDF's
Ermöglicht es mehrere .pdf Dateien zu einer Datei zusammenzuführen
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
### Inputvariablen:
- PDF-Files (MAP): Map<Order, Path/to/PDF/File.pdf> Führt die PDF's in der Entsprechenden Reihenfolge zusammen. Z.b.: [{1, /tmp/Deckblatt.pdf}{2, /tmp/Inhalt.pdf}]. Erzeugt ein neues PDF mit dem Inhalt von "Deckblatt.pdf", gefolgt im Inhalt von "Inhalt.pdf".
- Targetfile (STRING): Wohin das zusammengeführte PDF Exportiert werden soll.

</details>

## \[Table\] Create Table
  Erzeugt eine leere Tabelle mit den Designeinstellungen.
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
### Inputvariablen:

- TableWidth (NUMBER): Vollständige Breite der Tabelle
- Font (DEFAULT, HELVETICA, HELVETICA_BOLD, HELVETICA_BOLD_OBLIQUE, HELVETICA_OBLIQUE, COURIER, COURIER_BOLD, COURIER_BOLD_OBLIQUE, COURIER_OBLIQUE, SYMBOL, TIMES_BOLD, TIMES_BOLD_ITALIC, TIMES_ITALIC, TIMES_ROMAN, ZAPF_DINGBATS): Die Schriftart
- Font Size (NUMBER): Schriftgrösse [pt]
- FontColor (R,G,B): Die Farbe der Schrift im Format [R,G,B] Z.b. 255,128,64
- DoWordbreak (BOOLEAN): Der Text soll automatisch auf eine neue Zeile brechen, wenn er nicht in die Felder passt.
- VerticalAlignment (BOTTOM, MIDDLE, TOP): Vertikale Ausrichtung
- HorizontalAlignment (LEFT, CENTER, RIGHT, JUSTIFY): Horizontale Ausrichtung
- BackGroundColor (STRING): Die Farbe des Hintergrunds im Format [R,G,B] Z.b. 255,128,64
- BorderColor (STRING): Die Farbe des Randes im Format [R,G,B] Z.b. 255,128,64
- BorderStyle (SOLID, DOTTED, DASHED): Ob der Rand Solide, Gestrichelt, oder Gepunktet sein soll
- BorderWidth (NUMBER): Dicke des Randes [pt]
- Padding (NUMBER): Abstandhalter zwischen Zellenrand und Inhalt [pt]

### Outputvariablen:
- Table (OBJECT): Repräsentiert die leere Tabelle mit den Designeinstellungen. Diese muss noch mit Spalten befüllt werden.
 
</details>
  
## \[Table\] Add Column to Table
  Eine neue Spalte zur Tabelle hinzufügen
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
### Inputvariablen:

- Table (OBJECT): Die Tabelle, zu der die Spalte hinzugefügt werden soll.
- ColumnWidth (NUMBER): Die Breite der Spalte.
- Overridesettings (BOOLEAN): Die Designeinstellungen der Tabelle mit den unten eingestellten Einstellungen überschreiben. Falls dies nicht aktiv ist, muss nur die Tabelle, und Spaltenbreite angegeben werden.
- Font (DEFAULT, HELVETICA, HELVETICA_BOLD, HELVETICA_BOLD_OBLIQUE, HELVETICA_OBLIQUE, COURIER, COURIER_BOLD, COURIER_BOLD_OBLIQUE, COURIER_OBLIQUE, SYMBOL, TIMES_BOLD, TIMES_BOLD_ITALIC, TIMES_ITALIC, TIMES_ROMAN, ZAPF_DINGBATS): Die Schriftart
- Font Size (NUMBER): Schriftgrösse [pt]
- FontColor (R,G,B): Die Farbe der Schrift im Format [R,G,B] Z.b. 255,128,64
-  DoWordbreak (BOOLEAN): Der Text soll automatisch auf eine neue Zeile brechen, wenn er nicht in die Felder passt.
- VerticalAlignment (BOTTOM, MIDDLE, TOP): Vertikale Ausrichtung
- HorizontalAlignment (LEFT, CENTER, RIGHT, JUSTIFY): Horizontale Ausrichtung
- BorderColorLeft (R,G,B): Die Farbe des linken Randes im Format [R,G,B] Z.b. 255,128,64
- BorderColorRight(R,G,B): Die Farbe des rechten Randes im Format [R,G,B] Z.b. 255,128,64
- BorderStyleLeft (SOLID, DOTTED, DASHED): Ob der linke Rand Solide, Gestrichelt, oder Gepunktet sein soll
- BorderStyleRight (SOLID, DOTTED, DASHED): Ob der rechte Rand Solide, Gestrichelt, oder Gepunktet sein soll
- BorderWidthLeft (NUMBER): Dicke des Randes [pt]
- BorderWidthRight (NUMBER): Dicke des Randes [pt]

</details>
  
## \[Table\] Create Cell for insertion Into a Row
Um eine Reihe zu erzeugen, muss zuerst der Inhalt jeder Zelle erzeugt, und in eine Liste geladen werden.
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
### Inputvariablen:

- Content (STRING): Der Inhalt dieser Zelle
- Columnspan (NUMBER): Erlaubt es diese Zelle über mehrer Spalten zu verbinden. Um Spalten zu verbinden muss ein Wert von 2 oder Grösser angegeben werden.
- Rowspan (NUMBER): Erlaubt es dieser Zelle über mehrere Reihen zu verbinden. Um Reihen zu verbinden muss ein Wert von 2 oder Grösser angegeben werden.
- Overridesettings (BOOLEAN): Die Designeinstellungen der Tabelle, Spalte \& Reihe mit den unten eingestellten Einstellungen überschreiben. Falls dies nicht gesetzt ist, muss lediglich der Conten, und die Column/Rowspan angegeben werden.
- Font (DEFAULT, HELVETICA, HELVETICA_BOLD, HELVETICA_BOLD_OBLIQUE, HELVETICA_OBLIQUE, COURIER, COURIER_BOLD, COURIER_BOLD_OBLIQUE, COURIER_OBLIQUE, SYMBOL, TIMES_BOLD, TIMES_BOLD_ITALIC, TIMES_ITALIC, TIMES_ROMAN, ZAPF_DINGBATS): Die Schriftart
- Font Size (NUMBER): Schriftgrösse [pt]
- FontColor (R,G,B): Die Farbe der Schrift im Format [R,G,B] Z.b. 255,128,64
- DoWordbreak (BOOLEAN): Der Text soll automatisch auf eine neue Zeile brechen, wenn er nicht in die Felder passt.
- VerticalAlignment (BOTTOM, MIDDLE, TOP): Vertikale Ausrichtung
- HorizontalAlignment (LEFT, CENTER, RIGHT, JUSTIFY): Horizontale Ausrichtung
- BackGroundColor (STRING):Die Farbe des Hintergrunds im Format [R,G,B] Z.b. 255,128,64
- BorderColorTop (STRING):Die Farbe des oberen Randes im Format [R,G,B] Z.b. 255,128,64
- BorderColorBottom (STRING): Die Farbe des unteren Randes im Format [R,G,B] Z.b. 255,128,64
- BorderColorLeft (STRING): Die Farbe des linken Randes im Format [R,G,B] Z.b. 255,128,64
- BorderColorRight (STRING): Die Farbe des rechten Randes im Format [R,G,B] Z.b. 255,128,64
- BorderStyleTop (SOLID, DOTTED, DASHED): Ob der obere Rand Solide, Gestrichelt, oder Gepunktet sein soll
- BorderStyleBottom (SOLID, DOTTED, DASHED): Ob der untere Rand Solide, Gestrichelt, oder Gepunktet sein soll
- BorderStyleLeft (SOLID, DOTTED, DASHED): Ob der linke Rand Solide, Gestrichelt, oder Gepunktet sein soll
- BorderStyleRight (SOLID, DOTTED, DASHED): Ob der rechte Rand Solide, Gestrichelt, oder Gepunktet sein soll
- BorderWidthTop (NUMBER): Dicke des oberen Randes [pt]
- BorderWidthBottom (NUMBER): Dicke des unteren Randes [pt]
- BorderWidthLeft (NUMBER): Dicke des linken Randes [pt]
- BorderWidthRight (NUMBER): Dicke des rechten Randes [pt]  
### Outputvariablen:
- Cell (OBJECT): Die Fertige Zelle. diese muss in eine LIST hinzugefügt, werden.
</details>
  
  ## \[Table\] Insert TableRow into Table
  Eine Reihe von Zellen in eine Tabelle einfügen.
<details>
  <summary>Info (Klicken zum Anzeigen)</summary>
	
### Inputvariablen:
- Table (OBJECT): Die Tabelle, zu der die Reihe hinzugefügt werden soll.
- Rowdata (OBJECT) Benötigt eine List\<Cell\>. **Die Liste muss genau so viele Zellen enthalten, wie es Spalten gibt** (Ausser bei Zellenverbund, dort muss es mit den verbundenen Zellen aufgehen)
- Overridesettings (BOOLEAN): Die Designeinstellungen der Tabelle, Spalte mit den unten eingestellten Einstellungen überschreiben.
- Font (DEFAULT, HELVETICA, HELVETICA_BOLD, HELVETICA_BOLD_OBLIQUE, HELVETICA_OBLIQUE, COURIER, COURIER_BOLD, COURIER_BOLD_OBLIQUE, COURIER_OBLIQUE, SYMBOL, TIMES_BOLD, TIMES_BOLD_ITALIC, TIMES_ITALIC, TIMES_ROMAN, ZAPF_DINGBATS): Die Schriftart
- Font Size (NUMBER): Schriftgrösse [pt]
- FontColor (R,G,B): Die Farbe der Schrift im Format [R,G,B] Z.b. 255,128,64
- DoWordbreak (BOOLEAN): Der Text soll automatisch auf eine neue Zeile brechen, wenn er nicht in die Felder passt.
- VerticalAlignment (BOTTOM, MIDDLE, TOP): Vertikale Ausrichtung
- HorizontalAlignment (LEFT, CENTER, RIGHT, JUSTIFY): Horizontale Ausrichtung
- BackGroundColor (STRING): Die Farbe des Hintergrunds im Format [R,G,B] Z.b. 255,128,64
- BorderColor (STRING): Die Farbe des Randes im Format [R,G,B] Z.b. 255,128,64
- BorderStyle (SOLID, DOTTED, DASHED): Ob der Rand Solide, Gestrichelt, oder Gepunktet sein soll
- BorderWidth (NUMBER): Dicke des Randes [pt]
</details>
  

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung


