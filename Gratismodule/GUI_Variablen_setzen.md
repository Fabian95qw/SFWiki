---
title: Library zum setzen von GUI Variablen
description: 
published: true
date: 2021-12-06T14:05:44.160Z
tags: 
editor: markdown
dateCreated: 2021-12-06T13:59:46.396Z
---

# Beschreibung
Diese Modul Library ermöglicht es, GUI_Elemente innerhalb des Moduls mit neuen Werten zu befüllen und zu Speichern.

Somit können z.b. Dynamisch Werte nachgeladen werdem.
Ein paar Beispiele:

- Ende Jahres werden Automatisch die Feiertage des neuen Jahres im Modul nachgetragen.
- Ein Anrufer, welcher in dem Modul gelandet ist, wird automatisch in eine GUI_Liste von Blockierten anrufern aufgenommen.
- Ein Textfeld wird automatisch mit dem letzten Ergebnis eines Scripts befüllt.



# Modulbausteine
Das Modul enthält 3 Modulbausteine:

## GetModuleInstance4Edit
Erzeugt ein Modulinstanzproject. Dies repräsentiert das gleiche, wie wenn man in der GUI den Bleistift bei einer Instanz getätigt hat. Dieses Objekt muss mit den anderen Bausteinen verwendet werden.

### Inputvariablen:
- InstanceID (STRING): Die ID der Instanz die editiert werden soll. Für die eigene Instanz kann der Baustein "GetModuleInstanceId" (zu finden unter "STARFACE Entities") zur Ermittlung der ID verwendet werden.

### Outputvariablen:
- ModuleInstanceProject (OBJECT): Das Modulinstanzproject repräsentiert das gleiche, wie wenn man in der GUI den Bleistift bei einer Instanz getätigt hat. Dieses Objekt muss mit den anderen Bausteinen verwendet werden.
- Success (BOOLEAN): Gibt zurück, ob eine Instanz mit dieser ID gefunden wurde.

## SetFieldbyGUIName4Instance

### Inputvariablen

SaveChanges


# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung