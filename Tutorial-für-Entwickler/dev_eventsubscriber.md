---
title: Listener erzeugen
description: 
published: false
date: 2022-03-04T08:15:45.694Z
tags: 
editor: markdown
dateCreated: 2022-03-03T10:46:34.978Z
---

# Listener erzeugen

Module können passiv an Events im System zuhören, und dann aktionen ausführen.


## Tabelle von Listener

| Komponente | Zweck |
|------------|-------|
|            |       |
|            |       |
|            |       |

# 



## Listenertypen
### onPresenceChangedEvent
Dieses Event teilt, Änderungen am Präsenzstatus, sowie dem dazugehörigen Präsenzstatustextes mit.
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

### onModuleInstanceStateChangedEvent
Dieses Event feuert jedes mal, wenn eine Instanz eines Moduls de-aktiviert
Datenpaketinhalt:
- InstanceUUID (STRING): Die InstanceUUID, des Moduls, welches gerade de-aktiviert wurde
- IsEnabled (BOOLEAN): Ob die Instanz neu Ein-oder Ausgeschaltet ist.

### onLineStateChangedEvent
Dieses Event feuert jedes mal, wenn der Leitungsstatus zwischen On- und Offline wechselt.
Datenpaketinhalt:
- LineconfigId (STRING): Die Config ID der Leitung aus der DB
- LineName (STRING): Den Anzeigenamen der Leitung
- IsOnline (BOOLEAN): Ob die neue Leitung neu Online ist.