---
title: Gigaset N870 Klingeltöne Modul
description: 
published: false
date: 2022-06-16T11:24:05.026Z
tags: 
editor: markdown
dateCreated: 2022-06-14T09:06:16.883Z
---

# Beschreibung
Dieses Modul ermöglicht es, Klingeltöne für interne & externe Anrufe 4 zusätzliche Klingeltöne mit Filtermöglichkeiten für Anrufer und Angerufene Nummer zu definieren.

Zusätzlich können bis zu 4 eigene Klingeltöne hochgeladen werden.

# Konfiguration

## SUOTA
Dieses Modul benötigt dass SUOTA (The Software Update Over The Air)Feature, um die Klingeltöne auf die Handsets zu laden.
Dies kann mithilfe des Moduls aktiviert werden.
> Das Gigaset N870 muss danach neu provisioniert werden, um die Änderungen anzuwenden.{.is-info}


## Klingeltöne für interne & externe Anrufe
Es können jeweils ein Standardklingelton für interne & externe Anrufe ,sowie die dazugehörige Lautstärke festgelegt werden.

> Die Handsets müssen nach dieser Anpassung neu provisioniert werden!{.is-info}

## Klingeltöne nach Filter
Es können 4 paare von Ein- und Ausgehenden Nummernfiltern mit separaten Klingentönen definiert werden.

<details>
  <summary>Mögliche Formate (Aufklappen)</summary>

00491234567890 ==> Exakte Nummer
0049123456* ==> Alle Nummern die mit 0049123456 beginnen
*789 ==> Alle Nummern die mit 789 Aufhören
*123* ==> Alle Nummern die 123 irgendwo in der Nummer enthalten
12. ==> Alle dreistelligen Nummern, die mit 12 beginnen
.23 ==> Alle dreistelligen Nummern, die mit 23 aufhören
.2. ==> Alle dreistelligen Nummern, die mit einem Beliebigen Zeichen beginnen, eine zwei in der Mitte haben, und mit einem Beliebigen zeichen Aufhören.
... ==> Alle dreistelligen Nummern 
.23* ==> Alle Zahlen, die mit einer Zahl beginnen, darauf mit 23 Folgen, und danach mit Beliebig vielen Zeichen aufhören
</details>

> Die Handsets müssen nach dieser Anpassung neu provisioniert werden!{.is-info}

## Eigene Klingeltöne
Es können bis zu 4 eigene Klingeltöne auf die Handsets geladen werden. (**SUOTA muss aktiviert sein**)

Diese müssen im G722 Format mit der Endung .722 ins Modul hochgeladen werden.
Es gibt ein einfaches Tool für die Onlinekonvertierung: https://g711.org/
Das Zielformat auf "Asterisk G.722 (16Khz, Mono, G.722)" setzen.

> Die Handsets müssen nach dieser Anpassung neu provisioniert werden! Die provisionierung kann hierbei Aufgrund des SUOTA Updates mehrere Minuten dauern. {.is-info}

## Handset Provisioning
Um das Klingelton Feature zur verwenden muss aktuell auf jedem Handset der Provisionierungs-URL hinterlegt werden.
Dieser wird dynamisch vom Modul generiert.

> Bei weniger als 50% Batterie lässt sich die provisionierung nicht durchführen, ausser das Gerät befindet sich in einer ladeschale. {.is-warning}

> Die Handsets provisionieren sich nur einmal pro Tag! Wenn man Änderungen mehrmals provisionieren will, muss der N870 Dect Manager neu gestartet werden!{.is-warning}


# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung