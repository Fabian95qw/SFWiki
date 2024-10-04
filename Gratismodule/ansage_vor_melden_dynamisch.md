---
title: Ansage vor Melden mit dynamischem Text
description: 
published: true
date: 2024-10-04T08:16:24.834Z
tags: 
editor: markdown
dateCreated: 2024-10-04T07:39:58.495Z
---

# Beschreibung
Ein Ansage vor Melden Modul, bei dem die Texte dynamisch mit TTS generiert werden, um individuelle Texte für die Begrüssung zu erzeugen

# DSGVO

> Bei der Nutzung dieses Moduls werden Texte zur generierung entweder an STARFACE Spezifiche Server in Deutschland (bei STARFACE Stimmen) oder an OpenAI Spezifische Server in den USA gesendet (Bei OpenAI Stimmen) dies kann ggf. gegen ihre DSGVO verstossen. Die Firma SI-Solutions GmbH übernimmt hierfür keine Verantwortung! Bitte prüfen sie ausreichend, ob dieses Modul mit ihrer DSGVO vereinbar ist.
{.is-danger}

# Konfiguration

![1.png](/uploads/ansage_vor_melden_dynamisch/1.png)

## Sprecher
Hier kann der Sprecher gewählt werden, es gibt zwei STARFACE Stimmen (nur STARFACE Cloud) zur Auswahl, sowie alle aktuell Verfügbaren OpenAI Stimmen

## OpenAI Key
Der Schlüssel für die API der OpenAi.

## STARFACE Benutzer für Adressbuchsuche
Das Adressbuch wird im Namen dieses Benutzers durchsucht.

## Bei Direktrufen an Benutzer deren privates Adressbuch durchsuchen 	
Dursucht das private Adressbuch eines Benutzer, wenn er auf einer Direktwahl angerufen wird.

> Entfernen sie den Eintrag "private" aus der Tabelle "zu durchsuchende Adressbücher", damit nicht alle privaten Adressbücher durchsucht werden!
{.is-warning}

> Wenn der Angerufene nicht anwesend ist, und der Anruf weitergeleitet wird, so sieht auch der Benutzer/Gruppe an welche weitergeleitet wurde den aus dem privaten Adressbuch aufgelösten Kontakt
{.is-danger}

## Zu durchsuchende Adressbücher

Definiert welche STARFACE Adressbücher durchsucht werden sollen, dies ist entweder:

- Die Adressbuchnummer 1-10
- all: Für das Adressbuch 0
- private: Für die privaten Adressbücher aller User
- users: Für die STARFACE Benutzer

# Texte

![2.png](/uploads/ansage_vor_melden_dynamisch/2.png)

## Platzhalter
Im Text können Platzhalter hinterlegt werden, welche mit Informationen des Anrufers / Angerufenen ersetzt werden.
Folgende Platzhalter stehen zur Verfügung:

- firstname => Vorname
- lastname=> Nachname
- company => Firmenname
- targetname ==> Name des Ziels. Bei Benutzern der Vor & Nachname, bei Gruppen der Gruppenname
- number => Vollständig internationalisierte Rufnummer

## Unterschiedlicher Text pro Status
Das Modul kann pro Status Texte erzeugen, es unterscheidet basierend auf dem Telefoniestatus Erreichbar, Besetzt, DND/Ruhe und Offline

Man kann pro Status definieren, ob das Modul darauf reagieren soll oder nicht.

## Warteschlange
Man kann definieren, ob der Anrufer nach dem Text ine ine Warteschlange gelegt werden soll oder das Normale Klingeln hört, während die Zielperson angerufen wird.

## Konfiguration Texte

### Text Kunde im Adressbuch
Dieser Text wird genutzt, wenn der Anrufer im Adressbuch vorhanden ist.

Beispiel:
Guten Tag #firstname# #lastname#. Der Mitarbeiter #targetname# ist sofort für sie da. Bitte bleiben sie am Apparat.

Wird zu:
Guten Tag Otto Normalverbraucher. Der Mitarbeiter Max Mustermann ist sofort für sie da. Bitte bleiben sie am Apparat.

### Text Kunde nicht im Adressbuch
Dieser Text wird genutzt, wenn der Anrufer nicht im Adressbuch vorhanden ist.

Beispiel: 
Guten Tag. Der Mitarbeiter #targetname# ist sofort für sie da. Bitte bleiben sie am Apparat.

Wird zu:
Guten Tag. Der Mitarbeiter Max Mustermann ist sofort für sie da. Bitte bleiben sie am Apparat.

## Failover
Es kann eine Failover  Zielnummer im Modul hinterlegt werden, falls das Ziel nicht erreichbar ist.

### Maximale Wartezeit wenn vor Failover
Wie lange das Modul versucht den Anruf durchzustellen, bevor es auf den Failover übergeht.

### Failover Ziel
Die Zielrufnummer fürs Failover.

# Nummernfilter
Es muss definiert werden, auf welche Anrufer & Angerufene Nummern reagiert wird.
Dazu gibt es folgende Filtermöglichkeiten:

### Filtermöglichkeiten
Mögliche Formate:
00491234567890 ==> Exakte Nummer
0049123456\* ==> Alle Nummern die mit 0049123456 beginnen
\*789 ==> Alle Nummern die mit 789 Aufhören
\*123\* ==> Alle Nummern die 123 irgendwo in der Nummer enthalten
12\. ==> Alle dreistelligen Nummern, die mit 12 beginnen
.23 ==> Alle dreistelligen Nummern, die mit 23 aufhören
.2. ==> Alle dreistelligen Nummern, die mit einem Beliebigen Zeichen beginnen, eine zwei in der Mitte haben, und mit einem Beliebigen zeichen Aufhören.
... ==> Alle dreistelligen Nummern
.23\* ==> Alle Zahlen, die mit einer Zahl beginnen, darauf mit 23 Folgen, und danach mit Beliebig vielen Zeichen aufhören 

## Nummer des Anrufers Filter & Ausnahmen

![2.PNG](/uploads/zeitgesteuerte_umleitung_si/2.PNG)

Filter, welche hier gesetzt werden, werden auf die Nummer des Anrufers angewendet.

Er Prüft folgende Nummern:
- Externe Rufnummer des Anrufers
- Interne Rufnummer des Anrufers (Falls vorhanden)
- IFMC Rufnummer des Anrufers (Falls vorhanden)

## Nummer des Anrufers - Adressbuch & Ausnahmen

![8.PNG](/uploads/zeitgesteuerte_umleitung_si/8.PNG)

Die Anrufer können zusätzlich nach Adressbuch gefiltert werden.
Hierbei kann eine Liste von Adressbüchern, welche geprüft werden sollen mitgegeben werden.

> Falls die LDAP Anbindung aktiviert ist, müssen die Namen gemäss der Adressbucheinstellungen oder "all" für alle LDAP Adressbücher verwendet werden.
{.is-warning}

> Private Kontakte werden nicht durchsucht.
{.is-danger}


### Benutzer zum durchsuchen des Adressbuchs
Von STARFACE ist zum durchsuchen des Adressbuchs ein Benutzer vorgegeben, es wird einfach im Namen dieses Benutzers gesucht.


## Nummer des Angerufenen Filter & Ausnahmen
Filter, welche hier gesetzt werden, werden auf die Angerufene Nummer angewendet.
![3.PNG](/uploads/zeitgesteuerte_umleitung_si/3.PNG)

# Konfigurationen Exportieren/Importieren
![6.PNG](/uploads/zeitgesteuerte_umleitung_si/6.PNG)

Das Modul kann die Einstellungen per E-Mail Senden, und man kann sie wieder zurück in die Instanz laden.

> Die Exportdatei ist ein Serialisierter Java Objectstream. 
Auch wenn sie auf den ersten Blick lesbar aussieht, sollte sie auf keinem Fall von Hand editiert werden.
{.is-danger}


## Exportieren
Für den Export muss die E-Mail Adresse ausgefüllt werden, und der haken bei "Konfiguration per E-Mail senden" gesetzt sein. Man erhält dann eine \[UUID\].sfinstance. 

Die Datei kann ohne Probleme umbenannt werden. Die Endung .sfinstance muss aber behaltet werden!

## Importieren
Zum Importieren muss man einfach die .sfinstance Datei hochladen, unten den Haken "Konfiguration Importieren" Anhaken, **und das Modul Abspeichern (nicht Übernehmen)!**



# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung