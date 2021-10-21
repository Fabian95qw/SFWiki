---
title: Roundrobin
description: 
published: true
date: 2021-10-21T11:21:54.828Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:36:47.170Z
---

# Beschreibung
Das Roundrobin Modul verteilt Anrufe nach dem entsprechenden Prinzip in der Gruppe.
1. Ruf ==> Beginnt bei Tn.1 ==> Weiter zu Tn.2 ==> Weiter zu Tn.3
2. Ruf ==> Beginnt bei Tn.2 ==> Weiter zu Tn.3 ==> Weiter zu Tn.1
3. Ruf ==> Beginnt bei Tn.3 ==> Weiter zu Tn.1 ==> Weiter zu Tn.2

Hierbei lassen sich ebenfalls die maximale Anzahl Iterationen durch alle Teilnehmer definieren, wenn nun z.b. nach 2 Iterationen der Anruf immer noch nicht angenommen wurde, kann dieser im Modul noch weitervermittelt werden. 
# Konfiguration
![Roundrobin 1](/uploads/roundrobin/roundrobin-1.png "Roundrobin 1")

## Anzahl Iterationen
Definiert, wie oft das Modul durch alle Teilnehmer Rotiert, bevor es den Anruf weiterleitet.

## Anrufverteilung statt RoundRobin
Ändert die Funktion des Moduls wie folgt:
Das Modul Rotiert die Anrufe nicht mehr während sie klingeln. Stattdessen werden diese im Rotationsmodus an die User Verteilt, und es klingelt dann nur bei diesem einen User.

Beispiel:
1. Ruf ==> Beginnt bei Tn.1 ==> Bleibt bei Tn1, bis die Klingelzeit abgelaufen ist ==> Weiter zu Fehlgeschlagene Anrufe
2. Ruf ==> Beginnt bei Tn.2 ==> Bleibt bei Tn2, bis die Klingelzeit abgelaufen ist ==> Weiter zu Fehlgeschlagene Anrufe
3. Ruf ==> Beginnt bei Tn.3 ==> Bleibt bei Tn3, bis die Klingelzeit abgelaufen ist ==> Weiter zu Fehlgeschlagene Anrufe

## Fehlgeschlagene Anrufe weiterleiten an
Wenn ein Anruf nach den angegebenen Anzahl Iterationen immer noch nicht abgenommen wurde, wird es an diese Rufnummer weitergeleitet.

### Nummer
Der Anruf wird bei Fehlschlag in diese Nummer weitergeleitet

### Voicemailbox des ersten Angerufenen Nutzers
Der Benutzer wird an die Voicemailbox des ersten Users, der in dieser Iteration war weitergeleitet.

Bespiel im RoundRobin Modus:
1. Ruf ==> Beginnt bei Tn.1 ==> Weiter zu Tn.2 ==> Weiter zu Tn.3 ==> Geht auf Voicemailbox von Tn1
2. Ruf ==> Beginnt bei Tn.2 ==> Weiter zu Tn.3 ==> Weiter zu Tn.1 ==> Geht auf Voicemailbox von Tn2
3. Ruf ==> Beginnt bei Tn.3 ==> Weiter zu Tn.1 ==> Weiter zu Tn.2 ==> Geht auf Voicemailbox von Tn3


## Voicemail Pre-/Suf-fix
Wenn ein Benutzer mehrere Voicemailoxen hat, muss mit dem Pre-/Suffix zwischen den verschiedenen Voicemailboxen unterschieden werden. Ansonsten landet der Anruf eventuell auf der falschen Mailbox.

Beispiel:
Benutzer besitzt 3 Mailboxen:
- Mailbox 100
- HRN
- RR_Mailbox

Um sicherzustellen, dass die Anrufe vom Roundrobin auf der Mailbox RR_Mailbox landen, muss der Prefix RR_ gesetzt werden.

## Definition der Roundrobin Gruppe
![Roundrobin 2](/uploads/roundrobin/roundrobin-2.png "Roundrobin 2")

Nun muss einfach die Klingelstrategie auf die Roundrobin Gruppe geändert werden, und fertig.
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung