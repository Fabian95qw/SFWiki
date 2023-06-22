---
title: STARFACE 8.X Client Tipps & Tricks
description: 
published: false
date: 2023-06-22T12:21:44.509Z
tags: 
editor: markdown
dateCreated: 2023-06-20T09:42:31.829Z
---

# STARFACE 8.X Client Tipps & Tricks

Hier sind einige Tipps & Tricks für den neuen STARFACE 8.X Client.

## Standardworkspaces Editieren
Die Standardworkspaces sind normalerweise Vorgegeben, und können nicht editiert werden.
Durch Anpassung der Workspace.xml Files können auch die Standardworkspaces editierbar machen.

Die Workspace.xml Datei kann im Pfad: "C:\Users\\\[Benutzername\]\AppData\Roaming\STARFACE GmbH\winapp" gefunden werden.

Diese kann mit einem normalen Editor geöffnet & editiert werden.

Im Dokument müssen die Werte  \<Deletable>false\</Deletable> zu     \<Deletable>true\</Deletable> geändert werden.

Danach können die Standardworkspaces Editiert/Gelöscht werden.

> Der STARFACE Client muss geschlossen sein, ansonsten haben die Änderungen keinen Effekt!
{.is-warning}

## Workspace Icon's Ersetzen / Eigene Icon's einsetzen
