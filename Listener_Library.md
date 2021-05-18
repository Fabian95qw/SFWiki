---
title: Listener Library
description: 
published: false
date: 2021-05-18T08:31:16.207Z
tags: 
editor: markdown
dateCreated: 2021-05-18T07:24:22.585Z
---

# Beschreibung
Eine Library, von Listenern, welche nach der Registrierung die Daten an XML-RPC Einstiegspunkte weitergibt.

# Erstellung eines Listeners

## Listenertypen
### onPresenceChangedEvent
Dieses Event teilt, änderungen am Präsenzstatus, sowie dem dazugehörigen Präsenzstatustextes mit.
Datenpaketinhalt:
- STARFACE_ACCOUNT (NUMBER): STARFACE Account den es betrifft.
- Presence (STRING): Die Präsenz. Möglichkeiten sind: AVAILABLE, AWAY, DO_NOT_DISTURB, EXTENDED_AWAY, FREE_FOR_CHAT, UNAVAILABLE
- Presencemessage (STRING): Die Präsenznachricht.
- AvatarSha1Has (STRING): Der Sha1Hash des Avatars des Benutzers
- From (STRING): Die Quelle des Statuswechsels. Diese können z.b. so aussehen: 123/StarfaceAndroidClient, 321/Starface iOS Client, 567/Module

### onTelephonyStateChangedEvent
Dieses Event teilt die änderung am Telefoniestatus eines Benutzers mit.
Datenpaketinhalt:
- STARFACE_ACCOUNT (NUMBER): STARFACE Account den es betrifft.
- Telephonystate (STRING): Der neue Telefoniestatus. Möglichkeiten sind: ACTIVE, AVAILABLE, QUEUE_PAUSE, RINGING, UNAVAILABLE

### onDoNotDistrubSettingChangedEvent
Dieses Event teilt mit, wenn einen User seinen DND Status geändert hat.
Datenpaketinhalt:
- STARFACE_ACCOUNT (NUMBER): STARFACE Account den es betrifft.
- DND (BOOLEAN): DND ein(true)/aus(false)

### onNewCallStateEvent
Dieses Event wird bei jeder Änderung an einem aktiven Ruf ausgelöst. (Z.b. Neuer Anruf, Klingelt bei Teilnehmern, wurde Umgeleitet, wurde gehalten usw...)
Pro Anruf können mehrere Events gleichzeitig ausgelöst werden, da ein Event pro Teilnehmer ausgelöst wird.
Datenpaketinhalt:
- STARFACE_ACCOUNT (NUMBER): STARFACE Account zu dem diese Anrufinformation gehört
- AvatarHash (STRING): Der Avatar der Angezeigt werden soll
- CalledName (STRING): Name des Angerufenen
- CalledNumber (STRING): Nummer des Angerufenen
- CallerName (STRING): Name des Anrufers
- CalledName (STRING): Name des Angerufenen

## XML-RPC Einstiegspunkte


# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch/de/lizenzierung
