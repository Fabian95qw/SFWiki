---
title: Gruppen an/-ab-meldung blockieren
description: 
published: true
date: 2025-08-08T07:28:55.924Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:33:57.054Z
---

# Beschreibung
Das Modul ermögtlicht es die generelle An-/Ab-meldung, oder das Abmelden des letzten Mitglieds einer Gruppe zu verhindern.
Ebenfalls ist das generieren von E-Mails bei Verstössen möglich.

# Konfiguration

![config.png](/uploads/gruppeabmeldung-blockieren/config.png)

## Modus
Das Modul kanna auf Zwei Arten betrieben werden:

### Generelle Abmeldung an der Gruppe verhindern
Mitglieder können sich nicht von der Gruppe abmelden.

> Selbst Administratoren können keine Mitglieder mehr von der Gruppe abmelden, solange die Instanz aktiviert ist.
Neue Mitglieder anmelden ist möglich.
{.is-danger}

### Die Abmeldung des letzten Mitglieds verhindern
Sobald sich das letzte Mitglied der Gruppe versucht von der Gruppe abzumelden, wird dieses wieder angemeldet.

### Generelle Anmeldung an der Gruppe verhindern
Blockiert das Anmelden neuer Mitglieder, aber nicht das Abmelden an der Gruppe.

> Selbst Administratoren können keine Mitglieder mehr von der Gruppe abmelden, solange die Instanz aktiviert ist.
Neue Mitglieder anmelden ist möglich.
{.is-danger}

## Verstösse Melden
Je nach Modus wird ein Entsprechendes E-Mail generiert, wenn das Entsprechende Event Eintritt
Dieses Liefert per E-Mail folgende Infos:

- Datum
- AccountId
- Login
- Vor-/Nach-name

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung