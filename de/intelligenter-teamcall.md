---
title: Intelligenter Teamcall
description: 
published: true
date: 2021-04-07T13:52:44.383Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:34:33.932Z
---

# Beschreibung
Zeitersparende, einfache Konfiguration einer intelligenten Rufweiterschaltung für Abteilungs-Teams. Weiterleitung auf das Team und auf die persönliche Mailbox in Kombination möglich. Mit der integrierten IVR-Funktion kann sich der Anrufer automatisch auf die Zentrale verbinden lassen. 
# Konfiguration
![1](/uploads/intelligenter-teamcall/1.jpg "1")

## Begrüssung & Verarbeitung von Calls
Das Modul verarbeitet Anrufe, welche an dessen Rufnummer weitergeleitet wurden, diese müssen aber Zuvor bei einem Benutzer gewesen sein.
Also muss der Benutzer eine entsprechende Weiterleitung an das Modul gesetzt haben.

### Rufnummernanzeige
Anrufe die von einem Benutzer an das Modul weitergeleitet wurden können entsprechend gekennzeichnet werden. 
Bei der Rufnummernanzeige stehen mehrere Optionen zur Darstellung zur Verfügung.

### Ansage
Bevor der Anruf durch das Modul verarbeitet wird, kann gewählt werden, ob noch eine Ansage kommen soll, und ob der Anrufer in einer warteschlange Parkiert werden soll.

**Wichtig das Dropdown Menü music on hold füllt sich selbstständig mit den korrekten Einträgen. Dafür muss aber das Modul nach der aktivierung zwingend einmal gespeichert werden (nicht übernehmen)**

### Teams
Dem Modul muss eine Liste von Teams zugewiesen werden, welche er Verarbeiten soll. Hierbei muss in der Liste die Primäre Rufnummer der Gruppe eingetragen werden.
Aufgrund des **ursprünglich Angerufenen Benutzers** wird ermittelt, welche Gruppe als nächstes Angerufen werden soll. Hierbei ist die Priorität von oben nach unten.

Das Modul prüft in welchen Gruppen aus der Liste er Mitglied ist, und Ruft diese entsprechend an.

### Szenariowahl
Das Weitere vorgehen, falls der Anruf von keinem Gruppenmitglied abgenommen wurde.

### Abfrage Hilfsobjekte
Die Objekte Abfrage Gruppennummern / Abfrage Voicemailbox sind reine Hilfsobjekte, welche sich automatisch selbst mit den entsprechenden Infos aus der Starface versorgen. 
Diese Felder haben **keinen Einfluss auf die Modulfunktionalität**

### Erklärung Ablauf
Ein Benutzer, Max Mustermann (Interne Rufnummer 123) wird vom Otto Normalverbraucher auf seiner Direktwahl Angerufen, ist jedoch nicht am Platz.
Nach 15 Sekunden greift seine Zeitüberschr. Umleitung, und der Anruf wird an das Modul weitergeleitet.

Das Modul setzt den Anrufernamen auf 123 Max >> Otto Normalverbraucher (Rufnummernanzeige).
Otto Normalverbraucher erhält eine Ansage, dass der gewünschte Mitarbeiter nicht aktuell nicht erreichbar ist, und versucht wird ihn an sein Team zu vermitteln.  Anschliessend wird er in der Warteschlange platziert (Ansage vor Teamcalls).
Das Modul durchsucht nun die Liste der Teams nach einer Gruppe, in der Max Mustermann Mitglied ist. Bei der dritten Gruppe "Support" findet das Modul eine Mitgliedschaft für den Benutzer (Teams).
Nun Klingelt es 10 Sekunden bei der Gruppe Support. Die anderen Mitarbeiter der Gruppe sehen auf ihrem Display, dass via 123 Max, der Kunde Otto Normalverbraucher be ihnen Angekommen ist.

Wenn nun ein Mitglied der Gruppe den Anruf abnimmt, wird Max aus der Warteschlange geholt, und wird mit dem Mitarbeiter verbunden.  Das Modul ist somit fertig.
Wenn nun kein Gruppenmitglied abnimmt, wird der Anruf gemäss Szenario1/Szenario2 weiterverarbeitet (Szenariowahl).

![Diagramm 1](/uploads/intelligenter-teamcall/diagramm-1.png "Diagramm 1")

## Szenario1
![2](/uploads/intelligenter-teamcall/2.jpg "2")

Im Szenario 1 ist es möglich einen Text für ein IVR zu hinterlegen, und unten für die Verschiedenen Ergebnisse ein entsprechendes Ziel zu definieren.

### Spezialziel VOICEMAIL
Durch das Setzen des Textes "VOICEMAIL" beim Ziel wird das Ziel an die Voicemailbox des ursprünglich Angerufenen Benutzers weitergeleitet.

## Szenario2
![3](/uploads/intelligenter-teamcall/3.jpg "3")

Im Szenario 2 wird, falls Konfiguriert, ein weiterer Text abgespielt, gefolgt von einer Warteschlange.
Währenddessen versucht das Modul nun eine zweite, spezifische gruppe Anzurufen.

Beim Fehlschlag gibt es eine Möglichkeit, die Rufnummer an eine Voicemailbox zu verteilen.

### Bestimmte Mailbox
Der Anruf wird an die Mailbox die im Feld "Bestimmte Mailbox" gesetzt wurde weitergeleitet.

### Auf Voicemail Gruppe
Der Anruf wird an die Voicemailbox der Oben im "Zielgruppe Szenario 2" angegebenen Zielgruppe weitergeleitet.

### Auf Voicemail ursprüngl. DW
Der Anruf wird an die Voicemailbox des ursprünglich Angerufenen Benutzers weitergeleitet.

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch/lizenzierung
