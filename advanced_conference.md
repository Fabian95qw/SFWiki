---
title: Erweiterter Konferenzraum
description: 
published: true
date: 2025-05-14T08:56:28.360Z
tags: 
editor: markdown
dateCreated: 2025-05-14T08:43:53.398Z
---

# Beschreibung
Modul für einen erweiterten Konferenzraum, mit Moderationsfunktion im UCC-Client, sowie Statischen Login-PINs
# Konfiguration

![1.png](/uploads/advanced_conference/1.png)

## Raumnummer
Jedem Konferenzraum muss eine Raumnummer zugewiesen werden, in denen die Teilnehmer landen, es handelt sich hierbei nicht um eine Rufnummer für erreichbarkeit.

Wenn zwei Module die gleiche Raumnummer haben, landen sie im gleichen Konferenzraum, so können z.b. mehrere Teilnehmer PIN's für den gleichen Konferenzraum erzeugt werden.

## Raum hat einen Moderator
Der Konferenzraum kann Moderiert werden.
> Nur lokale STARFACE Benutzer können zu Moderatoren gemacht werden.
{.is-danger}


> Wenn der Konferenzraum Moderiert wird, werden Teilnehmer in einer Warteschlange platziert, bis der Moderator sich eingeloggt hat.
{.is-warning}

Ein Moderierter Raum erlaubt dem Moderator z.b. das Stummschalten/Entfernen von Teilnehmern.

![4.png](/uploads/advanced_conference/4.png)

## PIN's / PIN-Länge
Der Teilnehmer PIN muss zwingend gesetzt werden, der Moderator PIN muss nur gesetzt werden, wenn der Raum Moderiert wird.
Beide PIN's sollten die gleiche Länge haben, die muss entsprechend im Feld PIN-Länge angegeben werden.

# Konferenz Parameter
![2.png](/uploads/advanced_conference/2.png)

## Teilnehmer Stummschalten
Schaltet alle Teilnehmer (nicht den Moderator) automatisch Stumm, wenn sie den Raum betreten.
Der Moderator muss die Stummschaltung dann zuerst aufheben. Er kann den Moderator mit dem Standardmässigen \*2 darauf aufmerksam machen, dass er sprechen will.

In Unmoderierten Konferenzräumen muss der Teilnehmer selbst mit \*1 die Stummschaltung aufheben.

## Moderator Check
Definiert, wie oft das Modul prüft, ob der Moderator eines Konferenzraums anwesend ist, bevor er die Wartenden Teilnehmer in den Konferenzraum reinlässt.

## Warteschlange
Definiert, welche Warteschlangenmusik den Wartenden Teilnehmern abgespielt wird, während sie auf den Moderator warten.

# Konferenz Parameter (Global)
![3.png](/uploads/advanced_conference/3.png)

## Sounds de-/aktivieren
Das Modul erlaubt es die Sounds, welche die STARFACE beim Beitreten/Verlassen eines Konferenzraums abspielt zu deaktivieren.

> Dies ist eine Globale Konfiguration, sobald in einer Instanz diese Haken gesetzt wurden, beeinflusst dies Sämtliche Konferenzen, auch diese Ausserhalb des Moduls 
{.is-danger}



# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung