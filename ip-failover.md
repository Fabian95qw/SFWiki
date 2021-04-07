---
title: IP Failover
description: 
published: true
date: 2021-04-07T13:52:59.520Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:34:42.460Z
---

# Beschreibung
Schaltet Ihre Netzwerkinfrastruktur automatisch auf Ihren Not-Internetanschluss um, passt das Modul die notwendigen Einstellungen im Bereich Netzwerk NAT Ihrer Starface automatisch an und versendet gleichzeitig eine Alarmmeldung 
# Konfiguration
![Ipfailover](/uploads/ipfailover/ipfailover.png "Ipfailover")

## Checktimer
Der Checktimer definiert, in welchem Intervall jeweils die Prüfung der aktuellen externen IP ablaufen soll.
Wenn sich die IP geändert hat, passt das Modul diese in der Starface automatisch an.

## E-Mail & E-Mail Alamierung
Man kann definieren, ob, und weshalb man eine E-Mail erhalten soll.

### Änderung der IP Adresse
Das Modul informiert via E-Mail, über die Änderung der IP-Adresse auf der Anlage

### Fehlschlag beim Abrufen der IP-Adresse
Sollte das Modul es aus irgendeinem Grund nicht schaffen, seine eigene externe IP abzufragen, wird man entsprechend Alarmiert

## Events nach Änderung der IP-Adresse
Das Modul stellt zusätzliche Möglichkeiten zu Verfügung, nachdem die IP-Adresse geändert wurde.

### System neustarten
Fährt die Starface inkl. dem unterliegenden Betriebssystem durch

### Webserver neustart
Startet den Webserver, und die damit Verbundenen Dienste neu

### Asterisk neustart
Startet den Asterisk Dienst neu

### Leitungen neustarten
Startet den Leitungsdienst neu, dadurch versuchen sich sofort alle Leitungen wieder zu registrieren.
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch/lizenzierung