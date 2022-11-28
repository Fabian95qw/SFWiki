---
title: Eigene GUI Elemente via XML-RPC erzeugen.
description: 
published: false
date: 2022-11-28T15:03:38.785Z
tags: 
editor: markdown
dateCreated: 2022-11-28T14:10:31.575Z
---

# Eigene GUI Elemente via XML-RPC erzeugen.

> Bitte beachtet, ich habe nur sehr mässige Javascript kenntnisse, es gibt sicher bessere Methoden dies zu implementieren
{.is-danger}


## Konzept
Zuerst werde ich das Grundlegende Konzept hinter eigenen GUI-Elementen erklären.
Anders als die normalen GUI-Elemente werden diese mithilfe von Infotext Boxen Nachträgliche zum Modul hinzugefügt.
Die Infotextboxen erlauben es Standardmässig nur ganz bestimmte HTML-Tags wie z.b. "p, img, font, a" zu hinterlegen. alle anderen Tags u.a. auch das JavaScript \<script\> Tag werden beim Speichern automatisch entfernt.
Dies kann jedoch einfach Umgangen werden, somit können eigene Javascript , HTML & CSS Inhalte eingepflegt werden.

Diese neu Hinzugefügten Elemente, werden dann zwar dargestellt, aber müssen auch noch auf Informationen von der STARFACE zugreifen. hier kommen die XML-RPC Eintrittspunkte für die Module ins spiel.
Per JavaScript können Nachträglich per XML-RPC zusätzliche Informationen nachgeladen werden.
  
![Custom_UI_Elements.drawio.png](/uploads/dev_tutorial/Custom_UI_Elements.drawio.png)

### Stolpersteine

#### Inhalte Speichern
Wenn per XML-RPC Inhalte nachgeladen werden, müssen Änderungen an diesen Elementen irgendwie per XML-RPC an das Modul ebenfalls zurück ins  Modul geschrieben werden.

#### Tab-Wechsel
Die Inhalte im Modul sind extrem "flüchtig". Wenn der Modul Tab gewechselt werden Änderungen an normalen STARFACE Elementen in einen Temporären Cache gesichert, und die Webseite wird jedes mal, wenn man einen Tab ändert neu Gerendet und mit den Werten befüllt. Dies bedeutet, alles was mit JavaScript geladen wurde verfällt, sobald man im Modul den Tab wechselt.


<details>
  <summary>Bild (Klicken zum Anzeigen)</summary>
  
![tab_switching.gif](/uploads/dev_tutorial/tab_switching.gif)
  
</details>  

## Infotext HTML/CSS/JavaScript Injection
Wir verwenden dafür meinen Baustein "SetDescriptionByID".
[Download Modulbaustein](https://github.com/Fabian95qw/SF-Modulefunctions/raw/master/bin/modulefunction/setdescriptionbyid/SetDescriptionbyID.class)
[Download Source Code](https://github.com/Fabian95qw/SF-Modulefunctions/blob/master/src/modulefunction/setdescriptionbyid/SetDescriptionbyID.java)


