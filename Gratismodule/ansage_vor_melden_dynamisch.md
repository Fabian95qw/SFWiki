---
title: Ansage vor Melden mit dynamischem Text
description: 
published: false
date: 2024-10-04T08:05:47.600Z
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

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung