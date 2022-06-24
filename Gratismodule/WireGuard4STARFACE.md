---
title: Wireguard 4 STRARFACe
description: 
published: false
date: 2022-06-24T09:30:39.746Z
tags: 
editor: markdown
dateCreated: 2022-06-24T09:22:28.739Z
---

# Beschreibung
Ein Modul, welches direkt den WireGuard VPN auf der STARFACE installiert und via GUI Konfigurieren lässt.

# Konfiguration

## Name des Interface
Der Namen des Interface wird vom Modul automatisch vergeben, und kann nicht geändert werden.

## Status des Interface
Zeigt an, ob das Interface aktuell aktiviert ist oder nicht.
> Dies sagt nichts darüber aus, ob effektiv eine Verbindung auf diesem Interface aktiv ist! Dafür müssen die Interfaceinforamtionen ins Logfile geschrieben werden.{.is-warning}

## Public-Key
Der Public-Key zum generierten Private-Key des Interface. Dieser wird für Peers der Gegenstelle benötigt.

## Interfaceinformationen in Logfile schreiben.
Schreibt die Detailinforamtionen übers Interface ins Logfile. Hier sind u.a. auch die Peer Informationen sichtbar.

<details>
  <summary>Beispiel (Klicken zum Anzeigen)</summary>
  
#####################
\### Interface Information ###
#####################
interface: wg-2956b493
  public key: 5J04mixB9pNz58XK4z82PmFLkihRib2JLpDRkIWPVGk=
  private key: (hidden)
  listening port: 20000

peer: wPDLEKwxog6JH0bguynXX5MruCSeJaCVP96aKMzhHyE=
  endpoint: 192.168.200.187:20000
  allowed ips: 10.0.0.0/24
  latest handshake: 4 minutes, 21 seconds ago
  transfer: 18.28 KiB received, 50.75 KiB sent
  persistent keepalive: every 15 seconds

##################### 
  </details>
  
## Verbindung nach Neustart automatisch aufbauen
Sofern das Interface auf "Starten" steht, wird der Tunnel nach dem Systemneustart, oder Ähnlichem automatisch wieder aufgebaut.

## Interface
Hier erfolgt die Interfaceeinstellung gemäss WireGuard. 
Mehr Informationen, was hier einzurichten ist finden sie auf der WireGuard seite. https://www.wireguard.com/quickstart/

> Um Änderungen aus der GUI anzuwenden, muss das Interface gestoppt (Interface auf Stoppen + Speichern), und wieder gestartet (Interface auf Starten + Speichern) werden.
{.is-warning}

### PrivateKey
Der PrivateKey wird von der STARFACE beim **Speichern (nicht übernehmen)** des Moduls automatisch generiert, und anschliessend in die GUI geschrieben. Dieser darf nicht geändert werden.


# Peers
Hier können die Peers vom WireGuard Konfiguriert werden.

# Verbindung zwischen zwei STARFACE herstellen


# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung