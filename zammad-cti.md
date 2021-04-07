---
title: Zammad-CTI
description: 
published: true
date: 2021-04-07T11:37:49.007Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:37:43.372Z
---

# Beschreibung
Ein Modul zum Übergeben von Anrufinformationen ans Zammad System mithilfe der Zammad-CTI Generic Schnittstelle
# Flow
![Zammad Flow](/uploads/zammad-cti/zammad-flow.jpg "Zammad Flow")
# Konfiguration
## CTI (generic) aktivieren
Zur nutzung des Moduls muss ein Administrator im Zammad die CTI (generic) in den Einstellungen==> Integrationen aktivieren.
Der Endpunkt URL muss danach auf die STARFACE übertragen werden.

![Zammad Cti Activate](/uploads/zammad-cti/zammad-cti-activate.png "Zammad Cti Activate")

## Reaktion
![Zammad Reaction](/uploads/zammad-cti/zammad-reaction.png "Zammad Reaction")

### Gruppe für Reaktion
Die Gruppe, welche im Zusammenhang mit der "Weitergabe ans Zammad-CTI verwendet wird"

### Weitergabe ans Zammad-CTI

Es gibt 2 verschiedene Reaktionsarten, welche gesetzt werden können.
#### Anrufe an Mitglieder der Gruppe
Die Gruppe wird Technisch verwendet, es werden alle Anrufe, Von, und An diese Gruppenmitglieder ans Zammad weitergegeben. (Gemäss den gesetzten Haken)

#### Anrufe an Gruppennummer
Die Weitergabe ans Zammad findet nur auf der Gruppe statt, das heisst alle Eingehenden Anrufe an die Gruppe werden weitergegeben.

```diff
- In diesem Modus werden ausgehende Anrufe nie ans Zammad weitergegeben, und interne Anrufe werden nur weitergegeben, wenn die Gruppe angerufen wird.
```
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch/lizenzierung
