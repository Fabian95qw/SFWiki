---
title: Wireguard 4 STRARFACe
description: 
published: false
date: 2022-06-24T09:24:21.076Z
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
> Dies sagt nichts darüber aus, ob effektiv eine Verbindung auf diesem Interface aktiv ist!{.is-warning}

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



# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung