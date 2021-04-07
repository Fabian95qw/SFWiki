---
title: Quelle: Exchange Connector
description: 
published: true
date: 2021-04-07T11:38:31.561Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:38:26.068Z
---

# Beschreibung
Hier geht es Spezifisch um die Konfiguration des Exchange-Connectors im Adressbuch Importer
# Konfiguration
![Exchange Connector](/uploads/adressbuch-importer/exchange-connector.png "Exchange Connector")

## Importtyp
### Einzelimport

Wenn der Typ Einzelimport gewählt wird, werden die Untenstehenden Daten für den Import verwendet.

### Mehrfachimport
Wenn der Typ Mehrfachimport gewählt wird, werden die Untenstehenden Daten für die **ApplicationImpersonation** der Mehrfachimportliste verwendet. 

## Login Daten Exchange
Bei den Login Daten muss man aufpassen ob DOMÄNE\Benutzername oder benutzername@domäne für die Authentifizierung benötigt wird.

## EWS Url
Der EWS Url muss nur Angegeben, wenn es sich um einen Exchange Server handelt. Im Falle von Office365 muss dieser nicht Angepasst werden.

## Exchange Typ
Hier kann Zwischen Exchange Servern und Office365 unterschieden werden. 

## Kontakt Import Herkunftswahl

**Diese Konfiguration gilt nur beim Einzelimport**

### Private Kontaktordner
Der Ordnername wird in den Kontakten des angegebenen Benutzers gesucht.

### Öffentlicher Kontaktordner
Der Kontaktordnername muss einzigartig sein, damit diese gefunden wird. Ansonsten muss der Absolute Pfad vom Öffentlichen Verzeichnis ausgegeben werden, da sonst die erste Instanz des Ordnernamens gewählt wird.

**Beispiel bei dem der Ordnername ausreicht**
Position im Öffentlichen Verzeichnis. Gemeinsame Kontakte/Industrie/Lieferanten 
Hierbei reicht bereits der Kontaktordnername "Lieferanten" aus.

**Beispiel bei dem der Absolute Pfad benötigt wird**
Position im Öffentlichen Verzeichnis. *Gemeinsame Kontakte*/**Gemeinsame Kontakte**
Hierbei muss der ganze Pfad *Gemeinsame Kontakte*/**Gemeinsame Kontakte** angegeben werden, da er sonst *Gemeinsame Kontakte* statt **Gemeinsame Kontakte** wählt.

### Rekursionslimit
Mithilfe des Rekursionslimit soll verhindert werden, dass das Modul unnötige Ordner in der Öffentlichen Struktur nach dem Zielordner durchsucht.

### Freigegebenes Postfach
Das Modul meldet sich mithilfe des Angegebenen Benutzers am Freigegebenem Postfach an, und sucht dort nach dem Kontaktordner.
**Nicht Unterstützt ist sich mit einem Freigegebenem Postfach einzuloggen, und von dort aus die Öffentlichen Verzeichnisse zu durchsuchen.**
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch/lizenzierung