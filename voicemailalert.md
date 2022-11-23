---
title: Voicemail Alamierung
description: 
published: false
date: 2022-11-23T10:04:38.765Z
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

## Eskalationsstufen
Die Verschiedenen Eskalationsstufen, und die Nummer die Angerufen werden soll.
Das Modul beginnt bei der Eskalationsstufe 1, und geht dann fortlaufend zu den höheren Stufen, wenn die Maximale Anzahl Versuche pro Eskalationsstufe erreicht wurden.

# Annahme
Um zu verhindern, dass der Alarm auf einer Voicemailbox landet, muss dieser nach Abnehmen des Hörer mit einer DTMF bestätigt werden.

![3](/uploads/voicemailalert/3.png)

## Aufforderung zur Annahme der Nachricht.
Hier kann eine eigene Audiodatei für die Aufforderung zur Drücken der DTMF Taste hinterlegt werden.

Standardmässig ist eine Frauenstimme mit dem Text **"Es wurde ein Alarm ausgelöst. Drücken sie eine Beliebige Taste um anzunehmen"** hinterlegt.

## DTMF Taste zum Annehmen
Es kann definiert werden, ob eine beliebige DTMF Taste gedrückt werden kann, oder ob man eine Spezifische Taste oder sogar Tatstenkombination nehmen will

## Spezifische DTMF
Hier kann ein spezifischer DTMF Code hinterlegt werden z.b. 1234

## DTMF Länge
Es muss mitgegeben werden, wie lange der DTMF Code ist, oder wie viele beliebige DTMF Tasten gedrückt werden sollen, um das Voicemail anzunehmen

## DTMF Timeout
Wie lange das Modul auf die DTMF Tasten wartet, bevor es den Anruf als nicht Erfolgreich ansieht.


# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung