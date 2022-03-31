---
title: STARFACE File Explorer
description: 
published: false
date: 2022-03-31T11:32:43.626Z
tags: 
editor: markdown
dateCreated: 2022-03-31T11:16:51.548Z
---

# Beschreibung
Ein Modul, welches es ermöglicht auf die Dateinfrastruktur des Unterliegenden Betriebssystems von STARFACE zuzugreifen.

> Die Clientseitige Applikation benötigt Java
{.is-info}

# Download
Download Modul: http://module.si-solutions.ch/file-explorer/7.X/STARFACE_File_explorer_v151.sfm
Download Client: http://module.si-solutions.ch/file-explorer/7.X/File-Explorer.zip


# Konfiguration
Das Modul muss auf der Anlage importiert werden, und es muss eine Instanz erzeugt werden. 
Der Name der Instanz wird nachher im Client benötigt.

## Zugriff vom Client
Im Client muss der URL der STARFACE, sowie der Name der Instanz hinterlegt sein.
Unten muss ein valider STARFACE Login eingegeben werden.

> Active-Directory Logins sind nicht unterstützt.
{.is-danger}

Anschliessend kann man die Verbindung Testen, und abspeichern.

![Setup.png](/uploads/file-explorer/Setup.png)

Dateien können durch einen Doppelklick heruntergeladen werden.

## Einschränkungen
- Es können keine Dateien hochgeladen werden.
- Alle Dateien werden als TomCat User ausgeführt, bedeutet kein Zugriff auf Dateien/Verzeichnisse, welche Root zugriff benötigen.

## Beispiel

![Example.gif](/uploads/file-explorer/Example.gif)

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung