---
title: Eigene GUI Elemente via XML-RPC erzeugen.
description: 
published: false
date: 2022-11-28T14:35:44.091Z
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


