---
title: Library zum setzen von GUI Variablen
description: 
published: true
date: 2021-12-06T14:40:12.445Z
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

# Modulbausteine laden & verwenden

Der Baustein kann via: https://github.com/Fabian95qw/SF-Modulefunctions/raw/master/bin/libraries/guichanges/guichanges.rar heruntergeladen werden

In diesem .rar File enthält es drei Bausteine. diese müssen via "Resources" in das Modul geladen werden, in die sie Verwendet werden sollen.

![1.png](/uploads/gui-variablen-setzen/1.png)

Nachdem die Modulbausteine hochgeladen wurden, müssten diese im "Public" Bereich unter dem eigenen Modulnamen (Im Experten Modus) sichtbar werden.

![2.png](/uploads/gui-variablen-setzen/2.png)

# Modulbausteine
Die Details zu den drei Modulbausteinen

## GetModuleInstance4Edit
Erzeugt ein Modulinstanzprojekt. Dies repräsentiert das gleiche, wie wenn man in der GUI den Bleistift bei einer Instanz getätigt hat. Dieses Objekt muss mit den anderen Bausteinen verwendet werden.

### Inputvariablen
- InstanceID (STRING): Die ID der Instanz die editiert werden soll. Für die eigene Instanz kann der Baustein "GetModuleInstanceId" (zu finden unter "STARFACE Entities") zur Ermittlung der ID verwendet werden.

### Outputvariablen
- ModuleInstanceProject (OBJECT): Das Modulinstanzprojekt repräsentiert das gleiche, wie wenn man in der GUI den Bleistift bei einer Instanz getätigt hat. Dieses Objekt muss mit den anderen Bausteinen verwendet werden.
- Success (BOOLEAN): Gibt zurück, ob eine Instanz mit dieser ID gefunden wurde.

## SetFieldbyGUIName4Instance
Setzt ein Feld in der GUI basierend auf dem GUI_Namen auf einen neuen Wert.
> Die Änderungen, welche mit diesem Baustein gesetzt werden sind temporär, bis sie mit dem Baustein SaveChanges" abgespeichert werden.{.is-danger}

### Inputvariablen
- ModuleInstanceProject (OBJECT): Das Modulisntanzprojekt. welches vom "GetModuleInstance4Edit" erzeugt wurde
- GUI_NAME (STRING): Name des GUI_ELEMENT dass Editiert werden soll. Z.b. GUI_STRING_TEST
![3.png](/uploads/gui-variablen-setzen/3.png)
- Value (OBJECT) Der neue Wert, welcher in die GUI geschrieben werden soll. unterstützte Dateitypen sind: BOOLEAN,STRING,NUMBER,STARFACE_ACCOUNT,STARFACE_GROUP,STARFACE_USER,MAP,LIST

### Outputvariablen
- Success (BOOLEAN): Ob dieses GUI_ELEMENT gefunden wurde, und erfolgreich editiert wurde.
- VariableChanged (BOOLEAN): Sich der Wert in der Oberfläche geändert hat. Z.b. wenn der Wert "Test" mit "Test123" überschrieben wurde ==> True, wenn "Test" mit "Test" überschrieben wurde ==> False. Dies soll dabei helfen unnötiges speichern zu verhindern, wenn sich in der GUI nichts geändert hat.

## SaveChanges
Alle Änderungen, welche mit dem SetFieldbyGUIName4Instance vorbereitet wurden, müssen auch noch abgespeichert werden.
Dieser Baustein speichert die Änderungen ab.
> Das durch den Baustein ausgeführte Speichern löst automatisch den Eintrittspunkt "Instance Changed" aus! Falls ihr GUI_Elemente von einem "Instance Changed" Eintrittspunkt aus verwendet sollte unbedingt rücksicht auf "VariableChanged" genommen werden, um einen Loop zu verhindern.{.is-danger}

### Inpuvariablen
- ModuleInstanceProject (OBJECT): Das Modulisntanzprojekt. welches vom "GetModuleInstance4Edit" erzeugt und anschliessend mit SetFieldbyGUIName4Instance editiert wurde.

### Outputvariablen
- Success (BOOLEAN): Gibt zurück ob die Änderungen Erfolgreich gespeichert werden konnten.


![example.gif](/uploads/gui-variablen-setzen/example.gif)

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung