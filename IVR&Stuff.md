---
title: IVR&Stuff
description: 
published: true
date: 2021-05-05T12:12:25.404Z
tags: 
editor: markdown
dateCreated: 2021-05-05T11:08:21.154Z
---

# Beschreibung
Ein IVR Modul, mit einer grossen Anzahl Konfigurationsoptionen, und die möglichkeit unendlich Stufen zu erstellen

# Konfiguration

## Stufenkonfiguration
Jede Instanz des Moduls ist eine Stufe. Der Stufentyp muss jeweils im Tab "Konfiguration" definiert werden.

![config.png](/uploads/ivr&stuff/config.png)

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

![next-step-example.png](/uploads/ivr&stuff/next-step-example.png)

## Hilfsobjekte
An verschiedenen Stellen im Modul werden Hilfsobjekte aufgelistet, die einem gewisse Informationen liefern (z.b. Benutzer, Gruppen, Voicemailboxen, andere Stufen).
Diese Hilfsobjekte haben keine Auswirkung auf das Modul.

## Stufentyp: Klingeln
Bei diesem Stufentyp kann man einen Benutzer oder eine Gruppe wählen, welche Angerufen werden soll (Bitte den korrekten Stufentyp Klingeln:Benutzer/Klingeln:Gruppe  einstellen)
Es kann eine Klingelzeit definiert werden.
Wir diese erreicht, springt das Modul automatisch zu der Stufe welche bei "Anruf: Bei fehlschlag weiter zu Stufe:" gewählt wurde.

![ringing.png](/uploads/ivr&stuff/ringing.png)

## Stufentyp: Ansage & DTMF
In diesem Stufentyp kann eine Ansage abgespielt werden, und danach verschiedene aktionen ausgeführt werden.
Es gibt grundsätzlich zwei Optionen: die klassische DTMF Tabelle, oder die dynamische Weiterleitung.

![dtmf-option.PNG](/uploads/ivr&stuff/dtmf-option.PNG)

### DTMF aktivieren
DTMF können komplett deaktiviert werden, falls man nur eine Ansage abspielen will.
Dann wird die Ansage abgespielt, und danach greift sofort das "Bei Fehschlag/nur Ansage weite zu Stufe"

### DTMF Option: Tabelle
In der DTMF Tabelle können klassische Nummern hinterlegt werden, es gibt aber auch einige spezielle Funktionen.

![dtmf-table.PNG](/uploads/ivr&stuff/dtmf-table.PNG)

#### DTMF STANDARD
Wird links statt einer Nummer STANDARD geschrieben, wird diese aktion für alle nicht definierten DTMF Tasten ausgeführt. 
Z.b. wenn nur die DTMF Tasten 0-2 gebraucht werden, aber der Kunde die 9 eingibt.

#### Ansage Wiederholen
Wenn bei einem Tastendruck die Ansage wiederholt werden soll, muss rechts einfach WIEDERHOLEN reingeschrieben werden.

#### IVR Stufe
Um eine andere IVR-Strufe anzusprechen, muss es via STUFE:Instanzname eingesetzt werden.
Gross-Kleinschreibung muss beachtet werden!
Z.b. STRUFE:ANSAGE

#### Voicemailboxen
Um eine Voicemailbox anzusprechen muss einfach die entsprechende *9[Nummer] hinerlegt werden.

### DTMF Option: Dynamische weiterleitung
In diesem Modus werden die Nummern verwendet, um eine dynamische Weiterleitung zu erzeugen.
Damit wird aus einer Vorlagenummer + dem eingebenen DTMF eine Nummer zusammengesetzt und Angerufen.

Dies kann z.b. im zusammenhang mit Durchwahlen verwendet werden.

![dtmf-dynamic.png](/uploads/ivr&stuff/dtmf-dynamic.png)

## Stufentyp: Voicemail
Dieser Stufentyp schickt den Teilnehmer direkt an die hinterlegte Voicemail.



# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch/de/lizenzierung
