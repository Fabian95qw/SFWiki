---
title: Listener Library
description: 
published: true
date: 2021-08-27T13:49:24.939Z
tags: 
editor: markdown
dateCreated: 2021-05-18T07:24:22.585Z
---

# Beschreibung
Eine Library, von Listenern, welche nach der Registrierung die Daten an XML-RPC Einstiegspunkte weitergibt.

# How-To

## Erstellung eines Listeners
Um die Listener zu nutzen, müssen die aktiv durch die Modulinstanzen nachregistriert werden. Der Einfachste weg dies zu tun, ist einen Timer zu verwenden, der Z.b. 1 mal in der Minute versucht den Listener zu registrieren.

Wenn der Listener mit einer UUID bereits registriert wurde, wird er nicht erneut registriert.

Die funktion CreateListener verlangt folgende Inputs:
- ListenerUUID (STRING): Die UUID, die dieser Listener erhalten soll
- InstanceUUID (STRING: Die UUID der Instanz, dessen Einstiegspunkt verwendet werden soll.
- XML-RPC-Entrypointname (STRING): Der Name des XML-RPC-Einstiegspunktes
- ListenerType (Dropdown): Der Typ des Listeners. Die Einzelnen Typen werden weiter unten erklärt.

![createlistener.PNG](/uploads/listener_library/createlistener.PNG)

## Listener entfernen
Um einen Listener zu Entfernen, muss der Baustein "DeleteListener" mit der Listener_UUID, die entfernt werden soll aufgerufen werden.

## Flow

![Flow.jpg](/uploads/listener_library/Flow.jpg)

## XML-RPC Einstiegspunkt für den erhalt des Datenpakets konfigurieren
Damit der XML-RPC Einstiegspunkt die Daten vom Listener erhält, muss dieser korrekt konfiguriert sein.
Der Einstiegspunkt muss eine Input-Variable haben, welche "Data" heisst, und vom Typ MAP ist.
Diese Map wird dann mit den Daten befüllt.

![RPC-Entrypoints.PNG](/uploads/listener_library/RPC-Entrypoints.PNG)
![event_example.PNG](/uploads/listener_library/event_example.PNG)

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

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung
