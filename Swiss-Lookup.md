---
title: Swiss-Lookup
description: 
published: true
date: 2025-10-30T07:08:51.790Z
tags: 
editor: markdown
dateCreated: 2023-01-02T14:18:05.809Z
---

# Beschreibung
Dieses Modul macht einen Lookup gegen Schweizer Telefonbücher. 

Das Modul hat eine interne Datenbank, in denen bereits aufgerufene Einträge gespeichert werden können, damit sie nicht wiederholt bei den Telefonbuchanbietern abgefragt werden, da es dort Limitierungen zu den Anzahl anfragen pro Stunde/Tag/Monat gibt.

# Konfiguration

![1.png](/uploads/swiss-lookup/1.png)

## Lookup Timeout \[s\]
Definiert wie viel Zeit das Modul maximal aufwenden darf, um die Rufnummer gegen externe Telefonbücher aufzulösen. Sollte der Timeout erreicht werden, so wird der Anruf unaufgelöst weitergegeben.

## Adressbuch Prioritäten
Definiert, welches Adressbuch die höhere Priorität hat. 
Die Standardeinstellung ist: 
1. STARFACE
2. Intern
3. TelSearch

> Die Namen sind Case Sensitive, und müssen genau so eingegeben werden, ansonsten wird das Adressbuch nicht erkannt bzw. nicht verwendet.
{.is-warning}


Somit wird das STARFACE interne Adressbuch zuerst nach der Rufnummer durchsucht, bevor die Interne DB geprüft wird, und dann schlussendlich wird eine Anfrage bei Tel.Search<span></span>.ch ausgeführt.

## Aufgelöste Adressen in interner DB Speichern.
Sofern aktiviert, wird die Vollständige internationalisierte Rufnummer in einer internen DB abgespeichert.

## Interne DB - Funktionen

![2.png](/uploads/swiss-lookup/2.png)

Man kann entweder eine Rufnummer gegen die interne DB Abfragen, oder diese aus der internen DB löschen. Dies wird z.b. benötigt, wenn die CallerID geändert wurde, oder die interne Beschriftung generell nicht mehr stimmt.

> Zur Verwendung, muss die Funktion ausgewählt, der Suchbegriff eingegeben & das Modul abgespeichert (nicht übernommen) werden.
{.is-warning}


## Suchbegriff
Hier muss die Rufnummer ohne leerzeichen Vollständig internationalisiert eingetippt werden.

## Suchergebnis
Hier wird entweder die in der internen DB abgelegte CallerID angezeigt, oder es kommt eine Meldung, dass dieser nicht gefunden wurde.

# STARFACE Adressbuch Einstellungen

![3.png](/uploads/swiss-lookup/3.png)

## STARFACE Benutzer für Adressbuchsuche
Definiert, im Namen welches Benutzers im Adressbuch gesucht wird. Dies ist für die Öffentlichen Ordner nicht weiter relevant, lediglich wenn auch ein bestimmter privater Ordner nach Adressbucheinträgen durchsucht werden soll.

## Zu durchsuchende Adressbücher
Definiert, welche Adressbücher auf der STARFACE nach dieser Nummer durchsucht werden soll. Standardmässig sind alle Adressbücher aufgelistet.

## Standard CallerID überschreiben.

![4.png](/uploads/swiss-lookup/4.png)

Wenn das Modul den Adressbucheintrag im normalen STARFACE Adressbuch findet, überlässt das Modul die Formatierung der CallerID normalerweise der STARFACE bzw. es wird die unter Telefone ==> ID-Anzeige gesetzte CallerID verwendet.

Es kann jedoch definiert werden, dass das Modul eine eigene CallerID setzt, und somit die ID-Anzeige ausser kraft setzt.

## STARFACE Formatierung CallerID
Der Wert, welcher statt der Standard CallerID verwendet werden soll.

<details>
  <summary>Klicken zum öffnen</summary>
Mögliche Werte:
  
| Wert           | Kommentar                               |
|----------------|-----------------------------------------|
| number         | Vollständig internationalisierte Nummer |
| academic_title | Akademischer Titel                      |
| birthday       | Geburtstag                              |
| city1          | Stadt                                   |
| city2          | ''                                      |
| city3          | ''                                      |
| comment        | Kommentar                               |
| company        | Firma                                   |
| country        | Land                                    |
| country2       | ''                                      |
| e-mail         | E-Mail                                  |
| e-mail2        | ''                                      |
| familyname     | Nachname                                |
| firstname      | Vorname                                 |
| job_title      | Berufsbezeichnung                       |
| postcode       | PLZ                                     |
| postcode2      | ''                                      |
| postcode3      | ''                                      |
| state          | Bundesland                              |
| street         | Strasse                                 |
| street2        | ''                                      |
| street3        | ''                                      |
| title          | Titel                                   |
| url            | Webseite                                |
| url2           | ''                                      |

</details>
  
## Maximale Zeichenlänge der Werte
Für alle Werte, welche in der CallerID verwendet werden, muss jeweils die Maximale Zeichenlänge hinterlegt werden. Bei einer länge von 0 wird dieser nicht gekürzt.

### Beispiel:
CallerID Format: #lastname# #firstname# #company#

| Wert | Maximale Zeichenlänge|
|---|---|
| lastname | 6 |
| firstname | 0 |
| company | 10 |

Der Anrufer ist "Max Mustermann Musterfirma".
Der Vorname Max, wird nicht gekürzt, der Nachname wird auf 6 Zeichen "Muster" gekürzt, und der Firmenname auf "Musterfirm" gekürtzt. das Ergebnis wäre "Max Muster Musterfirm"

# Tel.Search<span></span>.ch Einstellungen

![5.png](/uploads/swiss-lookup/5.png)

## API-Key
Hier wird der von der Tel.search<span></span>.ch zur Verfügung gestellte API Key benötigt.
Einen API-Key kann man unter: https://tel.search.ch/api/getkey.en.html anfordern.

## Sprache der Ausgabe
Tel.search.<span></span>ch kann die Suchergebnisse in allen Landessprachen + Englisch liefern. Hier kann definiert werden, welche davon für die Suchergebnisse verwendet wird.

## Formatierung CallerID
Wenn der Anruf durch die Tel.Search.<span></span>ch aufgelöst wird, wir die CallerID entsprechend Formatiert. Hier können alle unter von Tel.Search.ch unter dem Link: https://tel.search.ch/api/help.en.html unter "Format of Response" angegebene Parameter verwendet werden.

> Die CallerID wird in diesem Format in die DB gespeichert. Nachträgliche Änderungen haben keine Einfluss auf bereits abgespeicherte Einträge. 
{.is-warning}

## Maximale Zeichenlänge der Werte
Für alle Werte, welche in der CallerID verwendet werden, muss jeweils die Maximale Zeichenlänge hinterlegt werden. Bei einer länge von 0 wird dieser nicht gekürzt.

### Beispiel:
CallerID Format: #name# #firstname# #org#

| Wert | Maximale Zeichenlänge|
|---|---|
| name | 6 |
| firstname | 0 |
| org | 10 |

Der Anrufer ist "Max Mustermann Musterfirma".
Der Vorname Max, wird nicht gekürzt, der Nachname wird auf 6 Zeichen "Muster" gekürzt, und der Firmenname auf "Musterfirm" gekürtzt. das Ergebnis wäre "Max Muster Musterfirm"

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung