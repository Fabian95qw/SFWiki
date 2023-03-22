---
title: Wireguard 4 STRARFACe
description: 
published: true
date: 2023-03-22T08:09:53.598Z
tags: 
editor: markdown
dateCreated: 2022-06-24T09:22:28.739Z
---

# Beschreibung
Ein Modul, welches direkt den WireGuard VPN auf der STARFACE installiert und via GUI Konfigurieren lässt.

> NICHT STARFACE CLOUD KOMPATIBEL{.is-danger}


# Konfiguration

![Config.PNG](/uploads/wireguard4starface/Config.PNG)

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
Mehr Informationen, was hier einzurichten ist finden sie auf der WireGuard Seite. https://www.wireguard.com/quickstart/

> Um Änderungen aus der GUI anzuwenden, muss das Interface gestoppt (Interface auf Stoppen + Speichern), und wieder gestartet (Interface auf Starten + Speichern) werden.
{.is-warning}

### PrivateKey
Der PrivateKey wird von der STARFACE beim **Speichern (nicht übernehmen)** des Moduls automatisch generiert, und anschliessend in die GUI geschrieben. Dieser darf nicht geändert werden.

# Peers
![Peers.PNG](/uploads/wireguard4starface/Peers.PNG)

Hier können die Peers vom WireGuard Konfiguriert werden.
Mehr Informationen, was hier einzurichten ist finden sie auf der WireGuard Seite. https://www.wireguard.com/quickstart/

# Verbindung zwischen zwei STARFACE herstellen
Um die Verbindung zwischen zwei STARFACE herzustellen, muss auf beiden das WireGuard Modul installiert sein.

Es müssen jeweils die Public-Keys, sowie IP-Adressen + Port des jeweilig anderen Endpunktes auf jeder STARFACE eingetragen werden.

> Das Modul öffnet keine Ports. Ports müssen selbser geöffnet werden, Oder es muss ein Port > 20000 gewählt werden.{.is-warning}

![p2psf1.PNG](/uploads/wireguard4starface/p2psf1.PNG)

![p2psf2.PNG](/uploads/wireguard4starface/p2psf2.PNG)

![p2psf1peer.PNG](/uploads/wireguard4starface/p2psf1peer.PNG)

![p2psf2.PNG](/uploads/wireguard4starface/p2psf2.PNG)

![pingtest.png](/uploads/wireguard4starface/pingtest.png)

# Wireguard Installation Repository URL's

Da sich die Repository URL's für die Installation des Wiregaurd sich regelmässig Ändert, sind die Repository URL's in der GUI anzupassen.

Der URL muss im Format: https://repo.almalinux.org/almalinux/\[Version\]/\[Typ\]/x86_64/os/
Eingetragen werden.

Z.b. die Aktuellen URLS sind:
\[AlmaLinux-BaseOS\]: https://repo.almalinux.org/almalinux/8.7/BaseOS/x86_64/os/
\[AlmaLinux-AppStream\]: https://repo.almalinux.org/almalinux/8.7/AppStream/x86_64/os/
\[AlmaLinux-PowerTools\]: https://repo.almalinux.org/almalinux/8.7/PowerTools/x86_64/os/
\[AlmaLinux-Extras\]: https://repo.almalinux.org/almalinux/8.7/extras/x86_64/os/

Es kann aber sein, dass in einigen Monaten die Version 8.7 abgekündigt wurde, und die Repositories nicht mehr verfügbar sind, dann müssen die URL's z.b. auf 8.8 geupdatet werden:

Die aktuellsten URL's findet man am einfachsten via: https://repo.almalinux.org/almalinux/

![repository.png](/uploads/wireguard4starface/repository.png)

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung