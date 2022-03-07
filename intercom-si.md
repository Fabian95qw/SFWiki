---
title: Intercom-SI
description: 
published: false
date: 2022-03-07T14:11:13.115Z
tags: 
editor: markdown
dateCreated: 2022-03-07T14:01:42.355Z
---

# Beschreibung
Ein kleines Modul, welches es erlaubt, via Modultaste eine Nummer anzurufen, wobei dessen Endgerät den Anruf automatisch entgegennimmt (Gegensprechstelle/Intercom)

> Das Modul Funktioniert nur mit physischen Telefonen, keine unterstützung für den UCC-Client (Weder als Anrufer noch als Angerufener)
{.is-danger}

# Konfiguration

![intercom-si.png](/uploads/intercom-si/intercom-si.png)

## Anzurufende Nummer
Die Nummer, welche Angerufen wird, wenn das Modul mithilfe der Funktionstaste aufgerufen wird.

## Endgeräte Typ
Hier wird definiert, was für ein Typ das Endgerät ist. 
Je nach Typ wir dein anderer SIP-Header für das automatische Annehmen definiert.

Standardmässig sind nur Yealink und SNOM Telefone unterstützt.
Sollte es sich bei dem Telefon um ein Drittanbieter Telefon handeln, so kann man dem Anruf einen, oder mehrere eigene SIP-Header mitgeben.

Da die STARFACE UI die Zeichen "<",">" und ";" nicht akzeptiert wurden diese durch die "\[\[", "\]\]" und "!!" ersetzt.

Beispiele von SIP-Headern:
| GUI Wert | Ergebnis |
|----------|----------|
|Alert-Info: \[\[http://localhost/\]\]!!info=alert-autoanswer| Alert-Info: \<http://localhost/\>;info=alert-autoanswer |
|Alert-Info: \[\[http://localhost/\]\]!!answer-after=0| Alert-Info: \<http://localhost/\>;answer-after=0 |

> Für nicht unterstützte Endgeräte wird kein Support geliefert.
{.is-danger}


## Benutzerzuweisung 
Um das Modul einem Benutzer zuzweisen, muss dem Benutzer eine Taste vom Typ "Module aktivieren" mit diesem Modul zugewiesen werden.

> Der Knopf Funktioniert auch, ohne dass der Benutzer das Recht "Module aktivieren" besitzt.
{.is-success}

![assignment.PNG](/uploads/intercom-si/assignment.PNG)

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung