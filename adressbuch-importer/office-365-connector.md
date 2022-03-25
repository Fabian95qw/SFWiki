---
title: Quelle: Office365 Connector
description: 
published: true
date: 2022-03-25T09:10:55.801Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:38:44.513Z
---

# Beschreibung

Hier geht es spezifisch um die Konfiguration des Office365-Connectors im Adressbuch Importer

# Vorsicht Abhängigkeit!
> **Dieses Modul setzt vorraus, dass das Modul "Microsoft Graph API Library" installiert ist.**
{.is-danger}

Dieses finden sie auf http://module.si-solutions.ch
# Konfiguration

![O 365 Connector](/uploads/adressbuch-importer/o-365-connector.png "O 365 Connector")

## Importtyp

### Einzelimport

Wenn der Typ Einzelimport gewählt wird, werden die Daten vom Importkonfiguration normal verwendet.

### Mehrfachimport

Wenn der Typ Mehrfachimport gewählt wird, werden die Daten von der Importkonfiguration bei der Liste von Usern importiert, welche beim Mehrfachimport angegeben wird.

## Erstellen von App-Login mit Clientsecret + Berechtigungen

Wie ein App-Login für Microsoft Exchange erstellt wird sehen sie http://wiki.si-solutions.ch/de/office-365-client-app

Die entsprechenden Werte müssen in die Felder im Modul eingetragen werden (App-Tenant-ID, App-ID, App-Secret)

### Korrekte Permissions
Dieses Modul benötigt zur korrekten ausführung folgende API-Permissions:

Contacts.Read (https://outlook.office365.com/Contacts.Read):Lesen von Kontakten für alle User
full_access_as_app (https://outlook.office365.com/full_access_as_app): Wird benötigt, da sonst die App keinen Zugriff auf Exchange als ganzes erhält. 
> Diese Permission ist zu finden unter: "Von meiner Organisation verwendete APIs" --> 
> Office 365 Exchange Online (Oder Resource ID: 00000002-0000-0ff1-ce00-000000000000 --> Anwendungsberechtigungen --> 
{.is-info}

![full_access_as_app_permission.png](/uploads/adressbuch-importer-office365/full_access_as_app_permission.png)



## Importkonfiguration
### E-Mail Adresse für Import
Der Office365 Connector nutzt die App-Zugangsdaten, um sich als diesen Benutzer anzumelden (**Applicationimpersination**), alle Aktionen im Exchange werden im Namen dieses Benutzers ausgeführt.

> Benutzer mit aktivierter Multi-Faktor Authentifizierung (MFA) werden nicht unterstützt!{.is-danger}


## Kontakt Import Herkunftswahl

> **Diese Konfiguration gilt nur beim Einzelimport**
{.is-info}

### Private Kontaktordner

Der Ordnername wird in den Kontakten des angegebenen Benutzers gesucht.

### Öffentlicher Kontaktordner

Der Kontaktordnername muss einzigartig sein, damit dieser gefunden wird. Ansonsten muss der Absolute Pfad vom Öffentlichen Verzeichnis ausgegeben werden, da sonst die erste Instanz des Ordnernamens gewählt wird.

**Beispiel bei dem der Ordnername ausreicht**

Position im Öffentlichen Verzeichnis. Gemeinsame Kontakte/Industrie/Lieferanten 

Hierbei reicht bereits der Kontaktordnername "Lieferanten" aus.

**Beispiel bei dem der Absolute Pfad benötigt wird**

Position im Öffentlichen Verzeichnis. *Gemeinsame Kontakte*/**Gemeinsame Kontakte**

Hierbei muss der ganze Pfad *Gemeinsame Kontakte*/**Gemeinsame Kontakte** angegeben werden, da er sonst *Gemeinsame Kontakte* statt **Gemeinsame Kontakte** wählt.

### Rekursionslimit

Mithilfe des Rekursionslimit soll verhindert werden, dass das Modul unnötige Ordner in der Öffentlichen Struktur nach dem Zielordner durchsucht.​

### Freigegebenes Postfach

Das Modul meldet sich mithilfe des Angegebenen Benutzers am Freigegebenem Postfach an, und sucht dort nach dem Kontaktordner.

**Nicht Unterstützt ist sich mit einem Freigegebenem Postfach einzuloggen, und von dort aus die Öffentlichen Verzeichnisse zu durchsuchen.**

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung
