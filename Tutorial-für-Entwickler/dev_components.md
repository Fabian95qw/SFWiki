---
title: STARFACE Komponenten
description: 
published: false
date: 2022-02-23T14:22:26.841Z
tags: 
editor: markdown
dateCreated: 2022-02-23T14:16:56.671Z
---

# STARFACE Komponenten
Eine Liste von STARFACE Komponenten, mit der Auflistung, für was diese im Programmieren verwendet werden kann.

| Komponente | Zweck |
|-----------|----------|
| AdressBookHandler.class | Alles rund ums STARFACE Adressbuch |
|           |          |           |          |
|           |          |           |          |

## AdressBookHandler.class
Der Adressbuchhandler, bietet den Zugriff auf die STARFACE Adressbücher.

### Beispielcode

		AddressBookHandler ABH = (AddressBookHandler)context.provider().fetch(AddressBookHandler.class); //Hole die Komponente
		AddressBookInterface ABI = ABH.getAddressBookInterface(); //Hole das Adressbuchinterface
    SearchBean SB = new SearchBean(); //Erstelle eine neue Suchanfrage
    SB.setAccountId(STARFACE_USER); //Die Suche muss im einem eines STARFACE Benutzers augeführt werden
    SB.setPageSize(Integer.MAX_VALUE); //Liefere ALLE ergebnisse auf einmal, 
    SB.setSearchBase("1"); //Suche im Adressbuch "1"
    SearchResult SR = ABI.search(SB, "", true); //Führe die Suchanfrage, ohne Suchbegriff aus
    