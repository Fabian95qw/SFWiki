---
title: STARFACE File Explorer
description: 
published: true
date: 2023-10-05T05:54:01.468Z
tags: 
editor: markdown
dateCreated: 2022-03-31T11:16:51.548Z
---

> Dieses Tool ist als Hilfsmittel für Administratoren gedacht, und sollte auf keinem Fall als permanent aktives Moduls eingesetzt werden. <br/> Wenn die Instanz nicht aktiv verwendet wird, sollte sie deaktiviert werden. <br/> Ansonsten erzeugt man unnötige Sicherheitsrisiken, denn das Modul erlaubt es JEDEM mit einem validen STARFACE Login auf die Betriebssystem ebene zuzugreifen.
{.is-warning}


# Beschreibung
Ein Modul, welches es ermöglicht auf die Dateinfrastruktur des unterliegenden Betriebssystems von STARFACE zuzugreifen.

Dies Funktioniert für alle STARFACE, inkl. STARFACE-Cloud.

> Die Clientseitige Applikation benötigt Java
{.is-info}

# Download
Download Modul: Neuste Version immer auf https://module.si-solutions.ch
Download Client: http://module.si-solutions.ch/file-explorer/7.X-8.X/File-Explorer.zip


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
- Der File Explorer Arbeitet unter dem Tomcat User. Dateien/Ordner, auf die der Tomcat keinen Zugriff hat können nicht eingesehen/heruntergeladen werden.
- Dateien die grösser sind, als der aktuell freie Arbeitsspeicher können nicht heruntergeladen werden, da die Verarbeitung via XML-RPC stattfindet, und die Datei vollständig in den RAM gelsen + Transkodiert werden muss, bevor wir diese per XML-RPC Senden

## Beispiel

![Example.gif](/uploads/file-explorer/Example.gif)

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung