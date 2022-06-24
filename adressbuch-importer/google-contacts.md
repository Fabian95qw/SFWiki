---
title: End of Life: Quelle: Google Contacts
description: 
published: true
date: 2022-06-23T06:10:30.189Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:38:34.426Z
---

> Dieses Modul funktioniert Seit einer Änderung mit dem OAuth Flow von Seiten Google nicht mehr. Aktuell gibts keine Lösung um dies wieder mit der STARFACE kompatibel zu machen.
{.is-danger}

# Beschreibung
Hier geht es Spezifisch um die Konfiguration von Google Contacts im Adressbuch Importer
# Konfiguration
## API Zugriff
**Der API Zugriff muss durch die Firma SI-Solutions GmbH zuerst genehmigt werden.**
Wenn der Zugriff genehmigt wurde, erhalten sie eine API-ID, und API-Schlüssel, welche in die entsprechenden Felder eingetragen werden müssen

Nach dem Eintragen des Schlüssels muss das Modul **abgespeichert** werden.
Dann generiert das Modul einen Autorisierungs-URL

![Gchowto 1](/uploads/adressbuch-importer/gchowto-1.gif "Gchowto 1")

Man muss nun den Autorisierungs-URL in einem Webbrowser öffnen, und sich dort mit dem Google Konto anmelden, und anschliessend den Zugriff zulassen.
Danach erhält man einen Autorisierungscode.

![Gchowto 2](/uploads/adressbuch-importer/gchowto-2.gif "Gchowto 2")

Der AutorisierungsURL muss nun im Modul eingetragen werden, und das Modul anschliessend **abspeichern**.

![Gchowto 3](/uploads/adressbuch-importer/gchowto-3.gif "Gchowto 3")

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung