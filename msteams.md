---
title: MS Teams Statusabgleich
description: 
published: true
date: 2021-04-07T13:47:04.405Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:35:31.049Z
---

# Beschreibung
Ein Modul, welches den Chatstatus zwischen der STARFACE und dem MS Teams Synchron hält

**AKTUELL IN BETA**

**Das Modul benötigt die MS-GRAPH-API Library! Diese kann gratis auf http://module.nucom.ch heruntergeladen werden**
**Vom der MS-GRAPH-API Library muss zwingend eine Instanz angelegt sein!"
# Konfiguration
![Msteamsconfig](/uploads/msteams/msteamsconfig.png "Msteamsconfig")

## Dienst
Ermöglicht es den Synchronisierungsdienst zu Stoppen

## Master
Bestimmt welche der zwei Plattformen als Master dienen soll

## Abgleichsintervall

Prüft, wie oft der Status zwischen den zwei Plattformen abgeglichen werden soll.

## Zu überwachende Gruppe
Der Status wird nur für Mitglieder dieser Gruppe überwacht.
**Wichtig! Die Benutzer werden mithilfe ihrer E-Mail Adresse mit dem Office365 Konto abgeglichen**

# Anbindung MS Teams
![Msteamsdevicelogin](/uploads/msteams/msteamsdevicelogin.png "Msteamsdevicelogin")

Das Modul benötigt einen Gerätecode-App-Zugriff auf die Office365 Plattform. Die entsprechenden ID's aus der App müssen hier hinterlegt werden

## App im Azure Active-Directory erstellen.

Für eine Anleitung zur erstellung der App, siehe: http://wiki.nucom.ch/office-365-devicelogin-app

## Benötigte Berechtigungen
Die Berechtigungen, welche die App benötigt wären:

![Msteams Permissions](/uploads/msteams/msteams-permissions.png "Msteams Permissions")

* openid ==> Das Modul darf einen Benutzer einloggen. Es wird im Namen dieses Benutzers auf die Teams Resourcen zugegriffen
* offline_access ==> Das Modul kann ohne einwirkung des Benutzers Arbeiten. Ansonsten wird der Zugriff nach einer Stunde unterbrochen
* Presence.Read ==> Das Modul darf den Status des Users, mit welchem es eingeloggt ist lesen.
* Presence.Read.All ==> Das Modul darf den Status anderer User lesen
* profile ==> Darf das Profil des eingeloggten Benutzers ansehen. Wird benötigt um die UUID für die Abfrage des Status zu extrahieren.
* Users.Read.All ==> Wird benötigt, um die E-Mail Adressen aller Benutzer aus dem Office365 zu lesen, und mit den STARFACE Benutzern zu Vergleichen & zu verknüpfen

## Authentifzierung des Moduls mithilfe eines Gerätecodes
Damit das Modul die Office365 Resourcen nun nutzen kann, muss es erstmalig mithilfe eines Gerätecodes authentifiziert werden.
Der Gerätecode findet man im Log, nachdem man die App-ID + Tenenat-ID hinterlegt hat + den Dienst auf "Starten" gestellt hat.

![Msteams Devicecode](/uploads/msteams/msteams-devicecode.png "Msteams Devicecode")

Der Gerätecode muss auf https://microsoft.com/devicelogin eingegeben werden, und anschliessend muss das Konto angemeldet werden, in dessem Namen das Modul arbeiten soll.

![Deviceauth Start](/uploads/msteams/deviceauth-start.png "Deviceauth Start")

![Deviceauth Part 2](/uploads/msteams/deviceauth-part-2.png "Deviceauth Part 2")

![Deviceauth Finish](/uploads/msteams/deviceauth-finish.png "Deviceauth Finish")
# Statusmapping
Die beiden Plattformen haben nicht die gleiche Anzahl Status, und haben Teils auch verschiedene Versionen des gleichen Status
Diese müssen jeweils auf einen Status für die andere Platform gemappt werden,

![Msteamsstatemapping](/uploads/msteams/msteamsstatemapping.png "Msteamsstatemapping")
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch/lizenzierung
