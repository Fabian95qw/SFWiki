---
title: Roundrobin
description: 
published: true
date: 2021-08-16T11:02:35.282Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:36:47.170Z
---

# Beschreibung
Das Roundrobin Modul verteilt Anrufe nach dem entsprechenden Prinzip in der Gruppe.
1. Ruf ==> Beginnt bei Tn.1 == >Weiter zu Tn.2 ==> Weiter zu Tn.3
2. Ruf ==> Beginnt bei Tn.2 ==> Weiter zu Tn.3 ==> Weiter zu Tn.1
3. Ruf ==> Beginnt bei Tn.3 ==> Weiter zu Tn.1==> Weiter zu Tn.2

Hierbei lassen sich ebenfalls die maximale Anzahl Iterationen durch alle Teilnehmer definieren, wenn nun z.b. nach 2 Iterationen der Anruf immer noch nicht angenommen wurde, kann dieser im Modul noch weitervermittelt werden. 
# Konfiguration
![Roundrobin 1](/uploads/roundrobin/roundrobin-1.png "Roundrobin 1")

## Anzahl Iterationen
Definiert, wie oft das Modul durch alle Teilnehmer Rotiert, bevor es den Anruf weiterleitet.

## Fehlgeschlagene Anrufe
Wenn ein Anruf nach den angegebenen Anzahl Iterationen immer noch nicht abgenommen wurde, wird es an diese Rufnummer weitergeleitet.

## Definition der Roundrobin Gruppe
![Roundrobin 2](/uploads/roundrobin/roundrobin-2.png "Roundrobin 2")

Nun muss einfach die Klingelstrategie auf die Roundrobin Gruppe geändert werden, und fertig.
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung