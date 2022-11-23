---
title: Voicemail Alamierung
description: 
published: false
date: 2022-11-23T09:58:19.538Z
tags: 
editor: markdown
dateCreated: 2022-11-23T09:44:28.591Z
---

# Beschreibung

Dieses Modul überwacht eine spezifische Voicemailbox auf neue Voicemails.
Wenn eine neue Voicemail ankommt, werden mehrere Benutzer gemäss einer Eskalatiosnstufe nacheinander angerufen. 
Wenn ein Benutzer den Anruf annimmt, wird er aufgefordert eine DTMF Taste zu drücken. Anschliessend wird ihm das Voicemail abgespielt.
Sind alle Eskalationsstufen durch, und der Anruf wurde nicht zugestellt, so wird ein Alarm E-Mail verschickt.

# Konfiguration

![1](/uploads/voicemailalert/1.png)

## Jetzt Ausführen
Prüft beim Speichern die Voicemailbox auf neue Nachrichten, und löst ggf. den ganzen Prozess aus.

## Zu überwachende Voicemailbox *9
Es muss eine Zielvoicemailbox für das Modul gewählt werden.
> Es überwacht nur den "Neu" Tab, der "Privat" und "Alt" Tab werden nicht überwacht.
{.is-warning}

## Auszuführender User
Voicemailboxen können nur im Namen eines Benutzers abgerufen werden, das Modul versucht in Namen dieses Benutzers auf die Voicemailbox zuzugreifen.

## Prüfungsintervall
In diesem Intervall wird auf neue Voicemails geprüft, standardmässig wird die Voicemailbox alle 5 Minuten überprüft.

# Eskalationsstufen

![2](/uploads/voicemailalert/2.png)

## Anzahl Versuche pro Eskalationsstufe
Wie oft versucht wird bei der Rufnummer einer Stufe anzurufen

## Anruf Klingelzeit \[s\]
Die Klingelzeit, bevor ein Anruf als nicht Erfolgreich gesehen wird

## Anruf Wartezeit\[s\] vor Wiederholung
Die Wartezeit bevor die Nummer erneut Angerufen wird, falls diese den Anruf nicht angenommen hat.

## Anzuzeigender Anrufername
Setzt die CallerID auf diesen Namen. So wird dieser z.b. in der STARFACE App angezeigt.
> Bei Anrufen an externe Nummer gibt es keine garantie, dass die CallerID so erhalten bleibt.
{.is-warning}

## Anzuzeigende Rufnummer
Die Rufnummer, welche das Modul ausgehenden Anzeigen soll.




# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung