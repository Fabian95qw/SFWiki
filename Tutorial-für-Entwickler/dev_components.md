---
title: STARFACE Komponenten
description: 
published: true
date: 2023-02-17T09:17:57.918Z
tags: 
editor: markdown
dateCreated: 2022-02-23T14:16:56.671Z
---

# STARFACE Komponenten
Eine Liste von STARFACE Komponenten, mit der Auflistung, für was diese im Programmieren verwendet werden kann.

Grundsätzlich ist im Modul alles möglich, was in der GUI auch möglich ist. Man muss lediglich rausfinden, wo man suchen muss.

Beispiele für einzelne Funktionen findet ihr im Ordner "Beispiele"

| Komponente | Zweck |
|-----------|----------|
| AdressBookHandler.class | - Kontakte erstellen/löschen/editieren <br/> - Im Adressbuch Suchen |
| AutoprovAuthMacsHandler | -Verwaltung der MAC-Adressen Whitelist der STARFACE |
| CATConnectorPGSQL.class | - Div. vordefinierte Abfragen aus der DB abrufen <br/> - Alle Rufnummern abrufen <br/> - Alle freien internen/extern Rufnummern abrufen <br/>  - Informationen über Benutzer und Telefonzuweisungen abrufen <br/> - Primäre Rufnummern für Benutzer/Gruppen abrufen <br/> ...
| FunctionKeyManager.class | - Funktionstasten erstellen/löschen/editeren
| GroupHandler.class | - Gruppen erstellen/löschen/editieren <br/> - Gruppenmitgliedschaften anpassen
| HandsetStateAggrgatorRegistry.class | - Verwaltung von Handset IPUI's |
| ModuleBusinessObject.class | - Viele der Funktionen von Modulbausteinen sind im Modulebusinessobject. <br/> - Anruf Annehmen <br/> - Konferenz erstellen <br/> Ausgehende Anrufe platzieren <br/> - Ruf und Channelinformationen abrufen <br/> - Aufzeichnung von Anrufen <br/> - Klingeltöne setzen <br/> - Music on Hold setzen <br/> - Audio Playback <br/> ... |
| ModuleRegistry.class | - Variablen/Konfigurationen von Modulinstanzen und Modulen editieren <br/> - Neue GUI-Elemente für Module erzeugen <br/> - Modulinstanzen de-atkvivieren <br/> - Module Updaten/löschen <br/> - Funktionen in anderen Modulen aufrufen (auch Private) <br/> - Dem Modul Rufnummern zuweisen/entfernen |
|NetworkConfigurationComponent.class | - Editieren aller Netzwerkkonfigurationen wie im Tab "Server ==>Netzwerk"
| PersonAndAccountHandler.class | - Alles, was im Tab "Benutzer" möglich ist <br/> - Benutzer erstellen/editieren/löschen <br/> - Berechtigungen der Benutzer editieren <br/> - DND Status setzen <br/> - Lizenztyp anpassen <br/> - usw...
| PhoneUtils.class | - Telefone neu provisionieren <br/> - Funktionstasten manuell auf Telefone übertragen | 
| RedirectBusinessObject.class | - Benutzer/Gruppenumleitungen de-aktivieren/editieren <br/>
|SecurityComponent.class| - Black/Whitelisting <br/> - Firewall Tables editieren  <br/>  - Generelle Einstellungen aus dem Tab "Sicherheit"
|SipAndPhonesHandler.class | -Telefone anlegen/editieren/löschen <br/> - IFMC Konfigurationen de-aktivieren/erstellen/editieren/löschen
| StarfaceEventService.class | - Zum Feuern von div. Events <br/> - Benutzer Chatstatusänderungen publizieren <br/> - Benutzer Telefoneistatusänderungen publizieren <br/> -  \[n]changedEvent können hier Abonniert werden
| Serverbusinessobject.class | -Anpassung der Einstellungen für die ECSTA-Konfiguration <br/> - Zeitserver <br/> - Informationen zu Serverlast |
|SystemUtils.class | - Div. Systemtools <br/> - Neustart von STARFACE oder einzelnen Diensten <br/> - De-Aktivierung des SSH Zugriffs <br/> - Ausführn von div. Systemscripts
| UserStateBusinessObject | - Aktuellen Benutzerstatus abfragen <br/> - Benutzeravatar Abrufen
| VCloudComponent.class | - Prüfen, ob aktuelle STARFACE eine Cloud ist
|VoicemailListBusinessObject | - Abrufen von Voicemailinformationen für Benutzer/Gruppen <br/> - Voicemails verschieben/löschen
| Wiresettingshandler. class | - Abrufen/Editieren der Allgemeinen Leitungskonfiguration <br/> - Interne Nummernblöcke lesen/erstellen/editieren/löschen <br/> SIP-Provider lesen/erstellen/editieren/löschen <br/> Leitungen lesen/erstellen/editieren/löschen inkl. Rufnummenrzuweisung <br/> |

