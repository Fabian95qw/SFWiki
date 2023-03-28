---
title: STARFACE Dokumentationsmodul
description: 
published: false
date: 2023-03-28T14:20:16.186Z
tags: 
editor: markdown
dateCreated: 2023-03-01T08:50:30.959Z
---

# Beschreibung

Dieser erzeugt für euch eine STARFACE Dokumentation im PDF Format.

Das Modul enthält über 100 Parameter, um das Design des PDF's anzupassen:

Unter anderem:

- Eigene Deckblätter, sowie Seitendesigns im Hoch und Querformat hochladen
- Die Schriftart wählen, oder eigene Schriftarten (.ttf) Dateien hochladen
- Einen Seitenzähler hinzufügen
- Texte auf den Seiten Platzieren
- Wählen, welche Attribute in der Tabelle Dargestellt werden (Z.b. Beim Benutzer, ob Vorname/Nachname/Login ect.. auf der Dokumentation stehen soll.
- Farben für Tabellenheader, Tabelleninhalt, Textelemente ect. definieren
- Positionierung der Tabellen für die erste, sowie folgeseiten Festlegen.
- Breite für jede individuelle Spalte festlegen
- Horizontale/Vertikale Positionierung des Tabelleninhalts
- Die Gesamte Konfiguration des Dokumentationsmoduls kann im Tab "Konfiguration ==> Konfiguration Exportieren/Importieren" Exportiert werden. Dies Exportiert die Modulkonfiguration inkl. Hochgeladenen Dateien, (Eigene Deckblätter, Folgeblätter, Schriftarten usw..), so dass ihr euer eigenes Design auch auf anderen STARFACE wieder importieren könnt, und nicht jedes mal das ganze Modul konfigurieren müsst.

# Konfiguration

## Erzeugung & Timer

Das Modul kann in Regelmässigen abständen, oder auf Wunsch eine Dokumentation erzeugen und per E-Mail Versenden, oder als Download Link zur Verfügung stellen.

> Zur erzeugung der Downloadlinks muss das Modul abgespeichert werden, wenn man das Modul wieder öffnet, und der Download link immer noch nicht vorhanden ist, muss man es nochmals schliessen und wieder öffnen.
Die erzeugung des Download Links hängt stark von der Leistung der STARFACE, und der Anzahl zu erzeugenden Seiten ab.
{.is-warning}

<details>
  <summary>Bild (Klicken zum Anzeigen)</summary>
  
  ![1.png](/uploads/documentation/1.png)
  
  </details>

## Blätter wählen
Hier kann definiert werden, welche Blätter überhaupt für die Dokumentation erzeugt werden sollen.
Mehr Details zu den verschiedenen Blättern finden sie weiter unten.


<details>
  <summary>Bild (Klicken zum Anzeigen)</summary>
  
  ![2.png](/uploads/documentation/2.png)
  
  </details>

## Konfiguration Sichern/Wiederherstellen

Da das Modul extrem viele Parameter hat, wurde der Einfachheit, eine Funktion verbaut, mit der man die Konfiguration exportieren kann.

Man erhält per E-Mail eine entsprechende .sfinstance Datei, diese kann im Modul dann wieder importiert werden.

Die Konfigurationen können auch auf anderen Anlagen importiert werden, so können z.b. eigene Vorlagen mit eigenen Deckblättern bequem eingespielt werden.


<details>
  <summary>Bild (Klicken zum Anzeigen)</summary>
  
  ![3.png](/uploads/documentation/3.png)
  
  </details>

# Seiten-Zähler, Design & Schriftart

## Seiten-Zähler
Man kann im Modul konfigurieren, ob und wie Seiten gezählt werden.
Hierbei kann festgelegt werden, ob der Zählen linksbündig, rechtsbündig oder zentriert sein soll.
Die Positin, ob es oben oder unten ist, ist via dem Y-Offset zu definieren. Mehr Informationen zu den Offsets finden sie unter: http://wiki.si-solutions.ch/de/Gratismodule/PDF-Toolbox


<details>
  <summary>Bild (Klicken zum Anzeigen)</summary>
	
  ![4.PNG](/uploads/documentation/4.PNG)
 	<br/>
	![5.PNG](/uploads/documentation/5.PNG)

  </details>
  
## Seitendesign

Es können ein eigenes Deckblatt, sowie Folgeblatt im Hochformat & Querformat gesetzt werden.
Diese müssen jeweils im A4 Format hoch und quer entsprechend Hochgeladen werden.
Werden keine eigene Designs hochgeladen, wird ein Standarddesign verwendet.

  <details>
  <summary>Bild (Klicken zum Anzeigen)</summary>
  
  ![6.png](/uploads/documentation/6.png)
  
  Links Vorlage , Rechts Ergebnis
  
  ![7.png](/uploads/documentation/7.png)
  
  </details>
  
 ## Schriftarten 
 
In der Dokumentation müssen zwei Schriftarten hinterlegt werden. Einmal Normal, sowie Bold.
Wenn CUSTOM gewählt ist, und keine Schriftart hinterlegt wird, lädt das Modul automatisch Arial und Arial-Bold.

Es können auch eigene TrueType Schriftarten (.ttf) hochgeladen werden. 

> Für problemen mit eigenen Schriftarten gibt es keinen Support
{.is-warning}

 
  <details>
  <summary>Bild (Klicken zum Anzeigen)</summary>
  
  ![8.png](/uploads/documentation/8.png)
  
  </details>

# Seitendesigns - Allgemeine Informationen

Die verschiedenen Seiten haben alle eine Vielzahl von gleichen oder ähnlichen Einstellungsmöglichkeiten, hier werden die allgemeinen Einstellungsmöglichkeiten gedeckt, spezifische Einstellungen sind unten in eigenen Kapiteln verfügbar.

## Seitenformat, Sortierung, Felder
Für jede Folgeseite können eigene Einstellungen was das Seitenformat angeht gesetzt werden.

  <details>
  <summary>Bild (Klicken zum Anzeigen)</summary>
  
  ![9.png](/uploads/documentation/9.png)
  
  </details>

### Seitenformat

Die Seite kann in Hoch oder Queformat gesetzt werden.

### Sortierungsspalte

Es muss eine Spalte, nach der der Inhalt Sortiert werden soll definiert werden.
Welche Spalten zur Sortierung bereitstehen, variiert je nach Blatt, um welches sich handelt.

### Sortierungsreihenfolge

Ebenfalls ist zu definieren, ob die Sortierungsreihenfolge Aufsteigend, oder Absteigens ist, also z.b. bei Alphabetisch A-Z, oder Z-A, bei Nummern 0-9, oder 9-0

### Felder 

Es können auf der Seite zusätzliche Texte platziert werden, diese werden nur auf der Ersten generierten Seite Angezeigt, Beispiel beim Benutzer:

  <details>
  <summary>Bild (Klicken zum Anzeigen)</summary>
  
  ![10.png](/uploads/documentation/10.png)
  
  ![11.png](/uploads/documentation/10.png)
  
  </details>


## Tabellendesign

# Deckblatt

## Felder Platzieren

## STARFACE Infos

## Tabelle Platzieren

## Tabellen Design
  
  
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung