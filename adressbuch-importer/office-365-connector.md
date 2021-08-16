---
title: Quelle: Office365 Connector
description: 
published: true
date: 2021-08-16T09:42:36.442Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:38:44.513Z
---

# Beschreibung

Hier geht es spezifisch um die Konfiguration des Office365-Connectors im Adressbuch Importer

# Vorsicht Abhängigkeit!
**Dieses Modul setzt vorraus, dass das Modul "Microsoft Graph API Library" installiert ist.**
Dieses finden sie auf http://module.nucom.ch/
# Konfiguration

![O 365 Connector](/uploads/adressbuch-importer/o-365-connector.png "O 365 Connector")

## Importtyp

### Einzelimport

Wenn der Typ Einzelimport gewählt wird, werden die Daten vom Importkonfiguration normal verwendet.

### Mehrfachimport

Wenn der Typ Mehrfachimport gewählt wird, werden die Daten von der Importkonfiguration bei der Liste von Usern importiert, welche beim Mehrfachimport angegeben wird.

## Erstellen von App-Login mit Clientsecret + Berechtigungen

Wie ein App-Login für Microsoft Exchange erstellt wird sehen sie http://wiki.nucom.ch/de/office-365-client-app
Dieses Modul benötigt zur korrekten ausführung folgende API-Permissions:


Contacts.Read (https://outlook.office365.com/Contacts.Read):Lesen von Kontakten für alle User
full_access_as_app (https://outlook.office365.com/full_access_as_app):Zugriff auf alle Exchange Web Services. Wird benötigt für Öffentliche Ordner / Freigegeben Postfächer. 
> Diese Permission ist zu finden unter: "Von meiner Organisation verwendete APIs" --> 
> Office 365 Exchange Online --> Anwendungsberechtigungen
{.is-info}


Die entsprechenden Werte müssen in die Felder im Modul eingetragen werden (App-Tenant-ID, App-ID, App-Secret)

## Importkonfiguration
### E-Mail Adresse für Import
Der Office365 Connector nutzt die App-Zugangsdaten, um sich als diesen Benutzer anzumelden (**Applicationimpersination**), alle Aktionen im Exchange werden im Namen dieses Benutzers ausgeführt.

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
