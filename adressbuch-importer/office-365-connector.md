<!-- TITLE: Quelle: Office365 Connector -->

# Beschreibung

Hier geht es Spezifisch um die Konfiguration des Exchange-Connectors im Adressbuch Importer

# Konfiguration

![O 365 Connector](/uploads/adressbuch-importer/o-365-connector.png "O 365 Connector")

## Importtyp

### Einzelimport

Wenn der Typ Einzelimport gewählt wird, werden die Daten vom Importkonfiguration normal verwendet.

### Mehrfachimport

Wenn der Typ Mehrfachimport gewählt wird, werden die Daten von der Importkonfiguration bei der Liste von Usern importiert, welche beim Mehrfachimport angegeben wird.

## Erstellen von App-Login mit Clientsecret

Wie ein App-Login für Microsoft Exchange erstellt wird sehen sie TODO: [hier]

## Importkonfiguration
### E-Mail Adresse für Import
Der Office365 Connector nutzt die App-Zugangsdaten, um sich als diesen Benutzer anzumelden, alle Aktionen im Exchange werden im Namen dieses Benutzers ausgeführt.

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

Mithilfe des Rekursionslimit soll verhindert werden, dass das Modul unnötige Ordner in der Öffentlichen Struktur nach dem Zielordner durchsucht.​

### Freigegebenes Postfach

Das Modul meldet sich mithilfe des Angegebenen Benutzers am Freigegebenem Postfach an, und sucht dort nach dem Kontaktordner.

**Nicht Unterstützt ist sich mit einem Freigegebenem Postfach einzuloggen, und von dort aus die Öffentlichen Verzeichnisse zu durchsuchen.**

# Downloads & Lizenzierung

Für Downloads besuchen sie bitte http://module.nucom.ch/

Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch:8018/lizenzierung
