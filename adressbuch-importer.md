---
title: Adressbuch Importer
description: 
published: true
date: 2024-11-20T07:24:45.484Z
tags: 
editor: markdown
dateCreated: 2021-04-07T12:02:50.899Z
---

# Beschreibung
Das Modul kann zeitgesteuert vollautomatisch von diversen Adressbuchquellen wie Exchange-Server, Office365, CSV-Dateien oder beliebigen Text-Quelldateien mit definierbaren Datenfeldzuweisung-Templates Adressdaten importieren. Zusätzliche Funktionen wie z.B. eine intelligente Duplikat-Erkennung, Importunterdrückung von Adressen ohne Telefonnummern und Leerfeldkorrektur des Namensfeldes sind bei Bedarf aktivierbar. Zudem besteht die Möglichkeit die erkannte Rufnummer automatisch mit Vorwahlen zu ergänzen oder bestimmte Zeichen wie Klammern und Leerstellen automatisch zu entfernen. So wird aus der Zeichenfolge +41 (0)71 727 18 18 die optimal formatierte Telefonnummer +41717271818 ins Starface-Adressbuch importiert. 
Bei jeder Ausführung wird auf Wunsch ein Bericht erstellt und dem Systembetreuer per Email zugesendet.

# Konfiguration
## Automatisierung
### Importtimer

Die Automatisierung ist das Kernstück des Moduls. Hier können die allgemeinen Einstellungen für das Modul festgelegt werden.

> Es sollten keine Zeiträume < als 1 Stunde genommen werden, dies kann langfristig zu div. Problemen führen.
{.is-danger}


![Automatisierung 1](/uploads/adressbuch-importer/automatisierung-1.png "Automatisierung 1")

### Adressbuchmanagement

**Zieladressbuch Leeren**
Leert das gegebene Zieladressbuch. Sollte das Zieladressbuch ein Privates Adressbuch sein, so leert er das Private Adressbuch des „Accounts für Automatisierung“.

**Duplikatserkennungslogik anwenden.**
Import die Adressen, und wendet Dabei die Konfigurierte Duplikatserkennungslogik an, um Duplikate zu erkennen und zu ersetzen.
Mehr dazu im Kapitel Duplikats Erkennung

**Account für Automatisierung**
Der Account für die Automatisierung ist der Account, mit dem die Adressbucheinträge erstellt werden. 
Hierbei muss es sich nicht um einen Admin Account handeln.
Dies ist weniger wichtig, wenn es sich um ein Öffentliches Adressbuch handelt. 
Jedoch beim Import in ein Privates Adressbuch wird das Adressbuch dieses Benutzers verwendet.
 
**Zieladressbuch**
Das Zieladressbuch, welches für die Aktion gewählt werden soll. Dies Referenziert auf die Ordnerkonfiguration von der Starface Adressbuchkonfiguration. 
Zu beachten ist das Adressbuch «0» entspricht dem Adressbuch «all» 
Automatisierung beim Speichern anwenden
```diff
- WICHTIG das Schreibrecht beim Zieladressbuch muss aktiviert sein!
```
![Adressbuch](/uploads/adressbuch-importer/adressbuch.png "Adressbuch")

**Automatisierung beim Speichern anwenden**
Wendet die aktuelle Konfiguration unabhängig vom Import-Timer sofort an. 
Wird vor allem zu Testzwecken benötigt.

### E-Mail Einstellungen
 
Hierbei handelt es sich um die E-Mail-Adresse des Benutzers, welcher alle nachfolgenden Fehlermeldungen & Reports erhalten soll.

### Spezialmails
 
**Ergebnisse der Duplikaterkennung als E-Mail Senden**
Generiert ein E-Mail mit einem CSV im Anhang, welches Aufzeigt welche Kontakte als Duplikat von welchem existierenden Kontakt erkannt wurden.
Mehr dazu im Kapitel Duplikats Erkennung

Beispiel Duplikaterkennung CSV in Excel geöffnet:
![Duplikat](/uploads/adressbuch-importer/duplikat.png "Duplikat")

**Ergebnisse der Importbedingungen als E-Mail Senden**
Es wir dein CSV mit den Kontakten generiert, die Aufgrund der Importbedingungen nicht Importiert wurden. Es werden ebenfalls die Felder markiert, welche der Grund für den Nicht-Import waren.
Mehr dazu im Kapitel Importbedingungen

Beispiel Importbedingungen in Excel geöffnet.
 ![Importfilter](/uploads/adressbuch-importer/importfilter.png "Importfilter")
 
### Alarme
**Alarm bei Fehlerhaftem Dateidownload**
Löst einen Alarm aus, wenn der Dateidownload vom FTP oder SMB Server fehlschlägt.

**Alarm, wenn das Leeren des Adressbuchs fehlschlägt**
Löst einen Alarm aus, wenn das Leeren des Adressbuchs fehlschlägt. Dieser Fehler tritt nur auf, wenn ein Ungültiges Zieladressbuch oder ein Adressbuch ohne Schreibrechte aufgerufen wird.

Wird nur benötigt, wenn das Adressbuchmanagement auf „Adressbuch leeren“ steht. 

**Import von 0 Kontakten als Alarm behandeln**
Wenn ein Export aus einer anderen Software fehlerhaft war, die CSV für den Download jedoch existiert, und von der Starface heruntergeladen wurde, schlägt diese Alarm, da keine Kontakte im File gefunden werden konnten 
(Vorsicht mit Header Zeile, wenn „Erste Zeile Ignorieren nicht gesetzt ist!)

**Alarm, wenn Exchange Connectorfehler**
Das fängt sämtliche Fehler in Bezug auf den Exchange Connector ab.

## Konfiguration der Quelle

Für die Konfiguration der individuellen Quellen siehe:

Exchange Connector: https://wiki.si-solutions.ch/adressbuch-importer/exchange-connector
Office365 Connector: https://wiki.si-solutions.ch/adressbuch-importer/office-365-connector
Datei Import FTP/SMB/HTTP(S)-Get: https://wiki.si-solutions.ch/adressbuch-importer/datei-import
Google Contacts: https://wiki.si-solutions.ch/adressbuch-importer/google-contacts
CardDAV: https://wiki.si-solutions.ch/adressbuch-importer/card-dav
Multi-VCard:  https://wiki.si-solutions.ch/adressbuch-importer/vcard
Pipedrive-CRM: https://wiki.si-solutions.ch/adressbuch-importer/pipedrive
FinCRM: https://wiki.si-solutions.ch/de/adressbuch-importer/fincrm

## Duplikatserkennung

![Duplikatskonfiguration](/uploads/adressbuch-importer/duplikatskonfiguration.png "Duplikatskonfiguration")

### Anzahl Übereinstimmungen
Die Anzahl Teile eines Kontaktes, die Übereinstimmen müssen, damit der Kontakt als Duplikat des anderen Kontaktes gezählt wird.
Kontakte welche als Duplikat erkannt werden, werden in die Duplikats Liste eingetragen, welche per E-Mail zugesendet wird.

### Logik
In der Logik wird bestimmt, welche Felder überhaupt bei der Duplikat Erkennung überprüft werden sollen.
Die Felder können die Werte „Zwingend“ , „Ja“ oder „Nein“ enthalten.
Die Zwingenden Felder müssen immer Übereinstimmen, damit es als Duplikat erkannt wird. (Wird auch zu den [n] Übereinstimmungen dazugezählt)
Die „Ja“ Felder müssen in [n] Übereinstimmungen übereinstimmen, damit es als Duplikat erkannt wird.
Die „Nein“ Felder werden generell ignoriert.

## Verschiebelogik
![Verschiebelogik](/uploads/adressbuch-importer/verschiebelogik.png "Verschiebelogik")

### Logik
Die Verschiebelogik kann genutzt werden, um Felder mit Werten von anderen Feldern zu befüllen.
Z.b. wenn der Vorname leer ist, kann der Firmenname dorthin verschoben werden.
Oder wenn jemand nur eine Mobiltelefonnummer aber keine Normale/Hausnummer hat, kann die Mobilnr. Ins Rufnummernfeld verschoben werden.

### Kopieren statt Verschieben
Der Wert wird in das Ziel Feld Kopiert statt Verschoben und bleibt somit im Alten Feld ebenfalls erhalten.

## Importbedingungen
Ungültige Kontakte, werden in die Ungültige Kontakte Liste eingetragen, welche per E-Mail zugesendet wird.

### Importbedingungen Telefon
Die Importbedingungen verhindern das Importieren von ungültigen Kontakten, welche  keine Telefonnummern besitzen.
 
### Logik
Die Logik wird verwendet, um Kontakte auszufiltern, welche gewisse Fehlende Felder haben.
Eine Liste mit den Fehlerhaften Kontakten wird per E-Mail zugestellt.
 
![Importbedingungen](/uploads/adressbuch-importer/importbedingungen.png "Importbedingungen")

## Nummernfilter
Wenn Nummern aus Fremdprogrammen importiert werden, welche nicht Starface Konform (Internationales Nummernformat) sind, können diese mithilfe des Nummernfilter korrigiert werden.
Der Nummernfilter erlaubt es, gewisse Nummernteile durch andere zu ersetzen.
Es wird immer nur das erste Vorkommen des Nummernteils ersetzt.
Zb: NummernTeil: 071 == Ersetzen durch: +41(71)
Nummer: 0715736071 wird zu +41(71)5736071

![Nummernfilter](/uploads/adressbuch-importer/nummernfilter.png "Nummernfilter")

### Regex
Der Nummernfilter unterstützt Regex. **Diese müssen immer mit REGEX: beginnen!**

**Beispiel**

Der REGEX : ^((\\+|00)4[0-9])\\(?0?([0-9]{2})\\)? auf Nummern Angewendet:

Ursprüngliche Nummer	                    

| Originale Nummer | Nach Regex |
|------------------|------------|
|+41712345678 | +41712345678 |
|+410712345678 |+41712345678 |
|+41(71)2345678 |+41712345678 |
|+41(071)2345678 | +41712345678|
|0049712345678|0049712345678 |
|0049(071)2345678 |0049712345678 |
|0049(71)2345678 | 0049712345678|
|00490712345678 | 0049712345678|


Zum editieren von Regex sollte ein Hilfsprogramm wie z.b. Regex101 Verwendet werden.

Regex101 Beispiele:

* Einfacher Schweizer Nummernfilter: https://regex101.com/r/kV3vW4/1
* Komplexer Regex für das Filtern von allen +4[0-9] Nummern, inkl. Filterung von Klammern, Abständen, sowie Bindestrichen: https://regex101.com/r/Yb6MUI/1

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung