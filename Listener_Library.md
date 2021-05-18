---
title: Listener Library
description: 
published: false
date: 2021-05-18T08:43:36.448Z
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
- CallUUID (STRING): Die UUID des Anrufs.
- STARFACE_ACCOUNT (NUMBER): STARFACE Account zu dem diese Anrufinformation gehört
- AvatarHash (STRING): Der Avatar der Angezeigt werden soll
- CalledName (STRING): Name des Angerufenen
- CalledNumber (STRING): Nummer des Angerufenen
- CallerName (STRING): Name des Anrufers
- CalledName (STRING): Name des Angerufenen
- GroupID (STRING): ID der Gruppe, zu der der Anruf gehört (Falls vorhanden)
- CallState (STRING): Zustand des Anrufs. Möglichkeiten sind: CCBS CONFERENCE_ACTIVE CONFERENCE_CONSULT CONFERENCE_INACTIVE CONNECTED CONSULT HANGUP INCOMING LOGIN_LOGOUT MUSICONHOLD_TEST OUTGOING PARKED RINGBACK RINGING VOICEMAIL_LINKED VOICEMAIL_MAIN
- CallChannels (LIST\<String\>): eine Liste der einzelnen CallChannels
- ConferenceRoomId (STRING): Die ID des Konferenzraums (Falls vorhanden)
- DoorlineCamUrl (STRING): Der URL zur Kamera für die Türsprechstelle (Falls vorhanden)
- DoorlineDTMFCode (STRING): Den DTMF Code, der Ausgelöst werden soll, um die Tür zu öffnen (Falls vorhanden)
- DoorlineImageProviderID (STRING): Die ID, des Kamerabildproviders. Wird für das Aufzeigen des Bilds auf Endgeräten benötigt (Falls vorhanden)
- Duration (NUMBER): Wie lange der Anruf schon aktiv ist
- ForwardCallerIdName (STRING): Name des ursprünglichen Angerufenen, falls der Anruf weitergeleitet wurde (Falls vorhanden)
- ForwardCallerIdNumber (STRING): Nummer des ursprünglichen Angerufenen, falls der Anruf weitergeleitet wurde. (Falls vorhanden)
- ForwardType (STRING): Weiterleitungstyp. Möglichkeiten sind: BLINDTRANSFER, BL_BACK, CFB, CFI, CFNR, CFU, NONE, PICKUP, TRANSFER (Falls vorhanden)
- JabberId (STRING): ???
- Peernames (STRING): Name der Endgeräte, die in diesen Anruf involviert sind
- ReferenceOfConsultation (STRING): ???
- SipCallIds (STRING): ???
- Timestamp (NUMBER): Die Uhrzeit in Millisekunden (Epoch Zeit).


## XML-RPC Einstiegspunkte


# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch/de/lizenzierung
