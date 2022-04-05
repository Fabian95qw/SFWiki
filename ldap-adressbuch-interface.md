---
title: LDAP Adressbuch Interface für das STARFACE Adressbuch
description: 
published: true
date: 2022-04-05T07:43:29.438Z
tags: 
editor: markdown
dateCreated: 2022-01-04T09:26:18.627Z
---

# Beschreibung
Dieses Modul ermöglicht es, das in STARFACE integrierte Adressbuch per LDAP bereitzustellen.
Die Adressen werden regelmässig aus dem Adressbuch in einem im RAM laufenden LDAP Server geladen.

# Kompatible/Getestete Modelle
Folgende Telefone/Systeme wurden von uns gegen das Modul getestet:

- SNOM D785
- SNOM D385
- Gigaset N720 
- Gigaset N870

# Konfiguration Modul

![ldap-config2.png](/uploads/ldap-adressbuch-interface/ldap-config2.png)

## Adressbuch neu laden
Das Adressbuch wird zur bereitstellung per LDAP in den RAM geladen, und ist keine Live-Ansicht, der STARFACE Adressen. Die Adressen müssen also regelmässig aus dem STARFACE Adressbuch neu in den LDAP Server geladen werden.

## Dienst
Ermöglicht es den internen LDAP Server zu starten/stoppen.

## LDAP Port
Der LDAP Port, auf dem der LDAP Server zur Verfügung stehen soll.
Bitte beachten sie, dass es sich hierbei um LDAP und nicht LDAPS handelt. Die Daten werden also in unverschlüsselter Form übertragen. Support für LDAPS ist aktuell noch in entwicklung.

> Der Port muss überhalb des 1000-er bereichs gewählt werden, da die ersten 1000 Ports nur mit Root-Rechten geöffnet werden können.
{.is-danger}

> Für die Verwendung in der STARFACE Cloud muss ein Port im Bereich 10000-20000 gewählt werden
{.is-success}

## STARFACE Benutzer für Adressbuchzugriff
Das Modul lädt die Adressbucheinträge für den LDAP Server im Namen dieses Benutzers aus dem Adressbuch.

## LDAP Zugriff

**Der LDAP Zugriff muss zwingend durch einen Benutzernamen und Passwort abgesichert sein.**
Dieser Benutzer wird für den Zugriff durch die Telelfone verwendet. Der Loginname ist immer cn=[Login]

Die einzelnen STARFACE Adressbücher können einzeln als LDAP Adressbücher gemappt werden. 
Dazu wird jeweils Links die Adressbuchnummer, und Rechts der Namen für das LDAP festgelegt. Mehr informationen dazu gibt es unten bei der Konfiguration des LDAP's auf den Telefonen.

![ldap-config3.png](/uploads/ldap-adressbuch-interface/ldap-config3.png)


## Arbeitsspeicher-Verbrauch
Bei den Tests ergab sich etwa das Folgende Verhältnis:

- 100 Kontakte: 1mb Arbeitsspeicher
- 1000 Kontakte: 10mb Arbeitsspeicher
- 10'000 Kontakte:100mb Arbeitsspeicher
- 100'000 Kontakte:1000mb Arbeitsspeicher

# Verwendete LDAP Attribute
Folgende LDAP Atrribute werden Verwendet/Befüllt:

- cn: Besteht aus Vorname, Nachname, Firmenname
- displayname: Besteht aus Vorname, Nachname, Firmenname 
- givenname: Vorname
- sn: Nachname
- telephonenNumber: Die Rufnummer
- telephoneNumber: Die primäre interne Rufnummer (bei STARFACE Benutzern)
- telephoneNumber: Die primäre externe Rufnummer (bei STARFACE Benutzern)
- homephone: Die private Rufnummer
- mobile: Die Mobiltelefonnummer
- description: Firmenname

# LDAP Konfiguration auf Telefonen
Damit die Telefone auf das LDAP Adressbuch Zugreifen kann, müssen geweisse Einstellungen an den Telefonen konfiguriert werden.

## Login
Der im Modul gesetzte Login muss auf den Telefonen in der Form cn=[Login] eingetragen werden.
Z.b. cn=Phone

## Base-DN
Die Base-DN des Adressbuchs auf der STARFACE beginnt immer **dc=starface,dc=pbx**
Wenn über alle Verzeichnisse gesucht werden soll, kann diese so beibehalten werden, ansonsten muss noch die OrganizationUnit gemäss Tabelle im Modul festgelegt werden.

Z.b.:
![ldap_folder_example.png](/uploads/ldap-adressbuch-interface/ldap_folder_example.png)

Um nun auf ein spezifisches Adressbuch zu zeigen würden die Base-DN's z.b. so aussehen:
- ou=Alle, dc=starface, dc=pbx
- ou=Verzeichnis 1, dc=starface, dc=pbx
- ou=Interne Benutzer, dc=starface, dc=pbx

## Searchstrings
Als Searchstrings empfehlen wir Folgende:

### Namensfilter
Namensfilter: (|(cn=%\*)(sn=%\*)(givenname=%\*)(description=%\*))
Erzeugt folgendes Verhalten: Sucht im Anzeigenamen, Vornamen, Nachnamen, sowie Firmennamen nach Begriffen, die mit der Suchanfrage beginnen.

### Nummernfilter
Nummernfilter: (|(telePhoneNumber=\*%\*)(homePhone=\*%\*)(mobile=\*%\*))
Erzeugt folgendes Verhalten: Sucht in Rufnummer, privater Rufnummer, Mobiltelefonnummer, primärer interner Rufnummer , primärer externer Rufnummer nach der Rufnummer, die den Suchbegriff irgendwo enthält.

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung