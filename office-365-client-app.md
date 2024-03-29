---
title: Office365 App mit ClientSecret erstellen
description: 
published: true
date: 2022-03-25T09:12:39.409Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:35:50.336Z
---

# Beschreibung
Zur Nutzung einiger Office365 Spezifischen Module wird ein "App Zugang" benötigt, welcher dem Modul erlaubt, Aufträge im Office365 zu erledigen. (Z.b. Exchange Zugriff)
Hier wird kurz beschrieben, wie man so eine Office365 App erstellt.
# Erstellung einer App
Als erstes muss man sich auf https://portal.azure.com mit einem **Globalem Admin** der Organisation einloggen.
Danach wechselt man in das Azure-Active-Directory ==> App-Registrations, und erstellt dort eine neue App.
(**Dies funktioniert auch ohne entsprechende Azure AD Lizenzen**)

![Create App](/uploads/office-365-client-app/create-app.png "Create App")

## App-ID + Tentant ID Sichern

Sobald die App erstellt wurde, speichert als erstes die Application (client) ID, sowie die Directory (tenant) ID.
Diese werden später im Modul benötigt.

![App Info](/uploads/office-365-client-app/app-info.png "App Info")

## Secret erstellen

Wenn man die App nun Editiert, kann man im Tab "Certificates & Secrets" nun ein Secret erstellen.
Dieses muss ebenfalls gesichert werden, damit wir es später im Modul nachtragen können.

![Create Secret](/uploads/office-365-client-app/create-secret.png "Create Secret")

## App-Berechtigungen vergeben

Damit das Modul das machen kann, was es soll, muss man dem eben erstellten App-Zugang noch Berechtigungen zuweisen. Diese können im Tab "API permissions" gesetzt werden.
Die benötigten Berechtigungen Variieren von Modul zu Modul. 
Gewisse Berechtigungen müssen durch einen Globalen Admin genehmigt werden.

> Für die korrekten Berechtigungen, prüfen sie bitte den Wiki-Artikel des entsprechenden Moduls. Der Screenshot unten ist nur als Beispiel gedacht
{.is-warning}


![Admin Consent](/uploads/office-365-client-app/admin-consent.png "Admin Consent")