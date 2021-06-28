---
title: Office365 Kalender Connector
description: 
published: true
date: 2021-06-28T12:27:42.060Z
tags: 
editor: markdown
dateCreated: 2021-06-28T12:11:18.220Z
---

# Beschreibung
Das Modul analysiert automatisch Kalendereinträge über die norminierte Schnittstelle vom Exchange-Server resp. Office 365 und setzt bei einem gefundenen Termineintrag den Chat-Status und den entsprechenden Text z.B. "13:00 - 15:15 Sitzung extern Muster AG" im UCC-Client. Die Abwesenheit kann zusätzlich als aktive Besetztanzeige auf den IP-Telefonen signalisiert werden. Die vorhandenen Kategorien im Outlook werden durch zusätzlich automatisch angelegte STARFACE-Kategorien ergänzt. So kann einfach die interne und externe Rufnummer auf eine Voicemail-Box oder auf eine Zielnummer umgeleitet werden. Die Zielnummern für die AUL-Funktion kann im Kalender-Eintrag einfach durch den Anwender definiert werden, z.B. mit der Zeichenfolge @extern: +41717271818. Ist die Sitzung vor dem definierten Zeitpunkt fertig, kann der Benutzer einfach aufeine definierte interne Nummer anrufen und die Einstellungen werden zurückgesetzt. 

Oder kurz Ausgedrückt:

* Abweseneit im Chat Setzen (Abwesend/DND/Offline)
* Indizierung der Telefontaste (Rot auf Apparaten Rot/Blau im UCC-Client/Webinterface)
* Setzen von Infos im Chatstatus
* Umleitungen/Voicemail intern/extern Aktivieren/Deaktivieren
* Extrahiert Nummernziele direkt aus dem Kalendertext mit @@Extern: @@Intern:


# Vorsicht Abhängigkeit!
**Dieses Modul setzt vorraus, dass das Modul "Microsoft Graph API Library" installiert ist.**
Dieses finden sie auf http://module.nucom.ch/

# Konfiguration
![1](/uploads/office365-kalender-connector/1.png "1")

### Dienst
Erlaubt es den Modulinternen Dienst zu Starten/Stoppen, ohne das Modul zu deaktivieren.

### Office365 Gruppe
Das Modul wird nur auf alle Mitglieder dieser Gruppe angewendet.
Jeder User der Gruppe braucht eine Korrekt konfigurierte E-Mail Adresse, da das Modul den Status des Kalenders für diesen Benutzer überprüft.

## Reaktion auf Kalendereintragssystem
Definiert auf welche Buchungstypen überhaupt reagiert werden soll. 
Dies beinhaltet:
- Ausser Haus
- Gebucht
- Mit vorbehalt
- An anderem Ort tätig
- Frei

## Funktionen bei Abwesenheit
### Funktionstastenindikator
Man kann Konfigurieren, ob die Funktionstasten bei Abwesenheit einen speziellen Status erhalten. 
**Bei der Option "Blau" werden die BLF's nur im UCC-Client Blau dargestellt! BLF's an den Telefonen sind dann Rot**

### Chatindikator
Wenn nun ein Kalendereintrag erreicht wird, erhält der Benutzer diesen Status im Chat.

### Statustexte
Das Modul erlaubt es, die Fomatierung des Stautstextes im UCC-Client frei zu wählen. Es können Variablen zum ersetzen verwendet werden.
Folgende Variablen stehen zur Verfügung:

!time! ==> Uhrzeit Von-Bis
!title! ==> Titel des Eintrags, oder "Privat", falls der Eintrag auf Privat gesetzt ist.
!type! ==> Der Typ des Eintrags Gebucht/Ausser Haus usw...
Das vordefinierte Format ist: [!time!] [!type!] !title!  welches so aussehen würde: [07:00-12:00] [Gebucht] Kunde ABC

## Alarme
Es gibt die Möglichkeit bei Problemen mit dem Exchange Connector, oder mit Umleitungszeieln eine E-Mail zu alamieren.

# Office365 Verbindung
![2](/uploads/office365-kalender-connector/2.png "2")

Um eine Verbindung mit dem Office365 herzustellen, muss eine ntsprechender App-Login erstellt werden.

Wie ein App-Login für Microsoft Exchange erstellt wird sehen sie http://wiki.nucom.ch/de/office-365-client-app
Dieses Modul benötigt zur korrekten ausführung folgende API-Permissions:

full_access_as_app (https://outlook.office365.com/full_access_as_app):Zugriff auf alle Exchange Web Services. Wird benötigt für Öffentliche Ordner / Freigegeben Postfächer. 
> Diese Permission ist zu finden unter: "Von meiner Organisation verwendete APIs" --> 
> Office 365 Exchange Online --> Anwendungsberechtigungen
{.is-info}

### Maximale Terminlänge
Definiert, wie lange ein Termin maximal sein darf. Je grösser dieser Wert ist, umso grösser ist der Bereich, in dem das Modul nach gültigen Kalendereinträgen suchen muss.
Somit erhöht sich auch die Last auf der STARFACE.
> Kurz gesagt: Je grösser die Terminlänge, umso grösser ist die Last auf der STARFACE.
{.is-danger}

# Outlook-Kategorien
Es gibt die Möglichkeit Mithilfe von Kategorien mit der Starface zu interagieren.

![3](/uploads/exchange-kalender-connector/3.png "3")

## Anwenden bei allen Kalendereinträgen
Diese Optionen werden automatisch für alle Kalendereinträge aktiviert.
### Outlook Kategorien aktivieren
Aktiviert die Grundfunktion für Outlook-Kategorien. 
Diese werden Automatisch durch das Modul im Outlook hinzugefügt.

### Funktionstasten immer Ansprechen
Die BLF's Indizieren immer Rot/Blau, unabhängig, ob dies per Kategorie gesetzt wurde.

### Gruppenumlt. Miteinbeziehen
Bei den Umleitungen, die der User per Kategorien setzt, die Gruppeumleitungen miteinbeziehen.

## Eigene Konfiguration
Hier können Spezifische Event's für alle Kalendereinträge erzwungen werden

### Umleitungen intern immer aktivieren 
Aktiviert die Umleitung "Immer" der Internen Nummern für alle Kalendereinträge.

### Umleitungen extern immer aktivieren 		
Aktiviert die Umleitung "Immer" der Externe Nummern für alle Kalendereinträge.

### Voicemail intern immer aktivieren 		
Aktiviert die Voicemail "Immer" der Externe Nummern für alle Kalendereinträge.

### Voicemail extern immer aktivieren 	
Aktiviert die Voicemail "Immer" der Externe Nummern für alle Kalendereinträge.

## Spezialkategorien
Erlauben/Verweigern von Speziellen Kategorien im Outlook

### _SF_Ignorieren
Mit dieser Kategorie wird ein Kalendereintrag von der Starface ignoriert.
Wenn dies auf einen bereits aktiven Termin angewendet wird, werden die Änderungen (Umleitungen,DND usw...) rückgängig gemacht.

### _SF_Funktionstasten_aktivieren
Kategorie zum erlauben der BLF-Indikation Rot/Blau

### _SF_DND_aktivieren
Kategorie, die es möglicht macht DND auf der Anlage zu aktivieren, wenn ein Termin ansteht.

## Erlaubte Voicemail Kategorien
Erlauben/Verweigern von Voicemail Kategorien im Outlook

### _SF_Voicemail_intern_aktivieren
Erlaubt es die internen Nummer auf eine Voicemailbox umzuleiten

### _SF_Voicemail_extern_aktiviern
Erlaubt es die externen Nummer auf eine Voicemailbox umzuleiten

## Erlaubte Rufumleitungs Kategorien
Erlauben/Verweigern von Voicemail Kategorien im Outlook

### _SF_AUL_intern_aktivieren 	
Erlaubt es Umleitungen für die internen Rufnummern zu setzen.

### _SF_AUL_extern_aktivieren 	
Erlaubt es Umleitungen für die externen Rufnummern zu setzen.

## Erlaubte Parametisierung
Ob die Parametisierung von Zielen durch setzen von @@Intern/@@Extern für Umleitungen erlaubt ist
### @@Extern: 		
Erlauben von Parametisierung des externen Umleitungsziels durch Platzieren des Tags @@Extern:[Nummer] im Text des Kalendereintrags

### @@Intern:
Erlauben von Parametisierung des internen Umleitungsziels durch Platzieren des Tags @@Intern:[Nummer] im Text des Kalendereintrags
# Beispiel
![4](/uploads/exchange-kalender-connector/4.png "4")

![5](/uploads/exchange-kalender-connector/5.gif "5")
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch/de/lizenzierung
