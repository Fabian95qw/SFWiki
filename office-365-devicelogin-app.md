---
title: Office365 App mit Gerätelogin erstellen
description: 
published: true
date: 2021-04-07T13:47:31.017Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:36:01.232Z
---

# Beschreibung
Zur Nutzung einiger Office365 Spezifischen Module wird ein "App Zugang" benötigt, welcher dem Modul erlaubt, Aufträge im Office365 zu erledigen. (Z.b. Exchange Zugriff)
Hier wird kurz beschrieben, wie man so eine Office365 App erstellt.
# Erstellung einer App
Als erstes muss man sich auf https://portal.azure.com mit einem **Globalem Admin** der Organisation einloggen.
Danach wechselt man in das Azure-Active-Directory ==> App-Registrations, und erstellt dort eine neue App.
(**Dies funktioniert auch ohne entsprechende Azure AD Lizenzen**)

![Create App](/uploads/office-365-client-app/create-app.png "Create App")
## Authentifizierungsplatform setzen
Um den Gerätelogin zugänglich zu machen, muss eine Platform bestummen werden.
Wir verwenden hierbei die Plattform für Mobilgeräte.

![Office 365 Devicecode Platform](/uploads/office-365-devicecode-app/office-365-devicecode-platform.png "Office 365 Devicecode Platform")

Zusätzlich müssen für die Verwendung im Zusammenhang mit der STARFACE zwei Werte im Manifest von Hand gesetzt werden.

![Office 365 Devicecode Implicit Flow](/uploads/office-365-devicecode-app/office-365-devicecode-implicit-flow.png "Office 365 Devicecode Implicit Flow")
## App-ID + Tentant ID Sichern

Sobald die App erstellt wurde, speichert als erstes die Application (client) ID, sowie die Directory (tenant) ID.
Diese werden später im Modul benötigt.

![App Info](/uploads/office-365-client-app/app-info.png "App Info")

## App-Berechtigungen vergeben

Damit das Modul das machen kann, was es soll, muss man dem eben erstellten App-Zugang noch Berechtigungen zuweisen. Diese können im Tab "API permissions" gesetzt werden.
Die benötigten Berechtigungen Variieren von Modul zu Modul. 
Gewisse Berechtigungen müssen durch einen Globalen Admin genehmigt werden.
**Für die korrekten Berechtigungen, prüfen sie bitte den Wiki-Artikel des entsprechenden Moduls. Der Screenshot unten ist nur als Beispiel gedacht**

![Admin Consent](/uploads/office-365-client-app/admin-consent.png "Admin Consent")
