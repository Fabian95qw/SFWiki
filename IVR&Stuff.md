---
title: IVR&Stuff
description: 
published: false
date: 2021-05-05T12:00:15.864Z
tags: 
editor: markdown
dateCreated: 2021-05-05T11:08:21.154Z
---

# Beschreibung
Ein IVR Modul, mit einer grossen Anzahl Konfigurationsoptionen, und die möglichkeit unendlich Stufen zu erstellen

# Konfiguration

//BILD HIER

## Stufenkonfiguration
Jede Instanz des Moduls ist eine Stufe. Der Stufentyp muss jeweils im Tab "Konfiguration" definiert werden.
Es gibt folgende Stufentypen:
- Klingeln:Benutzer
- Klingeln:Gruppe
- Dynamische Nummer
- Ansage & DTMF
- Voicemail

Details zu den entsprechenden Stufen finden sie weiter unten im Wiki-Artikel.

## Konfigurationen die hierher verweisen
Listet auf, welche anderen IVR&Stuff Module auf diese Instanz verweisen.
Dies dient als eine Information, änderung and dieser Liste hat keinen Einfluss auf das Modul.

## Verknüpfung von Stufen
Das Modul bietet die möglichkeit, andere Stufen als ziel zu definieren.
Diese Liste updatet regelmässig. Falls eine Instanz aus irgendeinem Grund fehlt, sollte es ausreichen, die aktuelle instanz abzuspeichern, und wieder zu öffnen.

//BILD HIER

## Hilfsobjekte
An verschiedenen Stellen im Modul werden Hilfsobjekte aufgelistet, die einem gewisse Informationen liefern (z.b. Benutzer, Gruppen, Voicemailboxen, andere Stufen).
Diese Hilfsobjekte haben keine Auswirkung auf das Modul.

## Stufentyp: Klingeln
Bei diesem Stufentyp kann man einen Benutzer oder eine Gruppe wählen, welche Angerufen werden soll (Bitte den korrekten Stufentyp Klingeln:Benutzer/Klingeln:Gruppe  einstellen)
Es kann eine Klingelzeit definiert werden.
Wir diese erreicht, springt das Modul automatisch zu der Stufe welche bei "Anruf: Bei fehlschlag weiter zu Stufe:" gewählt wurde.

## Stufentyp: Ansage & DTMF

### DTMF Optionen
Folgende DTMF Optionen können definiert werden:

#### DTMF aktivieren
DTMF können komplett deaktiviert werden, falls man nur eine Ansage abspielen will.
**WICHTIG! Die DTMF dürfen nur im Zusammenhang mit der DTMF-Option Dynamische weiterleitung deaktiviert werden!**

#### DTMF Option: Tabelle
In diesem Modus wird eine Normale Tabelle für die Verarbeitung der DTMF Verwendet.

### DTMF Tabelle 
In der DTMF Tabelle können klassische Nummern hinterlegt werden, es gibt aber auch einige spezielle Funktionen.
#### DTMF STANDARD
Wird links statt einer Nummer STANDARD geschrieben, wird diese aktion für alle nicht definierten DTMF Tasten ausgeführt. 
Z.b. wenn nur die DTMF Tasten 0-2 gebraucht werden, aber der Kunde die 9 eingibt.

#### Ansage Wiederholen
Wenn bei einem Tastendruck die Ansage wiederholt werden soll, muss Rechts einfach WIEDERHOLEN reingeschrieben werden.

#### IVR Stufe
Um eine andere IVR-Strufe anzusprechen, muss es via STUFE:Instanzname eingesetzt werden.
Gross-Kleinschreibung muss beachtet werden!
Z.b. STRUFE:ANSAGE


#### DTMF Option: Dynamische weiterleitung



# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch/de/lizenzierung
