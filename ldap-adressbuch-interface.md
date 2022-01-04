---
title: LDAP Adressbuch Interface für das STARFACE Adressbuch
description: 
published: true
date: 2022-01-04T09:33:46.620Z
tags: 
editor: markdown
dateCreated: 2022-01-04T09:26:18.627Z
---

# Beschreibung
Dieses Modul ermöglicht es, das in STARFACE integrierte Adressbuch per LDAP bereitzustellen.

# Konfiguration Modul


# LDAP Konfiguration auf Telefonen
Damit die Telefone auf das LDAP Adressbuch Zugreifen kann, müssen geweisse Einstellungen an den Telefonen konfiguriert werden.

## Base-DN
Die Base-DN des Adressbuchs auf der STARFACE beginnt immer **dc=starface,dc=pbx**
Wenn über alle Verzeichnisse gesucht werden soll, kann diese so beibehalten werden, ansonsten muss noch das Entsprechende Unterverzeichnis gemäss Tabelle im Modul festgelegt werden.

Z.b.:


## Searchstrings
Als Searchstrings empfehlen wir Folgende:


# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung