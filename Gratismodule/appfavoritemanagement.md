---
title: App-Favoriten Management
description: 
published: true
date: 2026-02-27T10:00:07.459Z
tags: 
editor: markdown
dateCreated: 2026-02-12T15:33:00.743Z
---

# Beschreibung
Das Modul erlaubt das Kopieren von Favoriten Tasten zu Telefon Funktionstasten für Alle User, einzelne Gruppen, oder für User-Self Service via Anruf.

Zusätzlich erlaubt das Modul ein oder mehrere Gruppen von Favoriten von einem Benutzer zu einer Abteilung zu übertragen.

Und als letztes erlaubt es auch Funktionstastenebereiche in Favoriten zu verwandeln.

# Konfiguration App-Favoriten zu Telefon-FK

![1.png](/uploads/appfavoritemanagement/1.png)

## Beim Speichern / Übernehmen anwenden
Wendet die Einstellungen sofort an, statt Zeitgesteuert oder Self-Service

## Favoriten zu Funktionstasten übertragen für:
Definiert ob die Favoriten für alle Benutzer oder nur für eine Gruppe von Benutzern auf die Funktionstasten übertragen werden soll.

## Favoriten kopieren:
Definiert, ob nur eine gewisse Kategorie gemäss dessen Namen oder alle Favoriten's kopiert werden.

![2.png](/uploads/appfavoritemanagement/2.png)

## Kategoriename
Der Name der Kategorie, falls nicht alle Kategorien kopiert werden sollen

## Telefone provisionieren
Ob die Tischtelefone der User neu provisioniert werden sollen.

## Offset
Ein Basisoffset vom Start der Funktionstasten für alle Tasten

![3.png](/uploads/appfavoritemanagement/3.png)

## Self-Service für User
Wenn dem Modul eine Rufnummer zugewiesen wird, können User dort anrufen.
Das Modul beantwortet den Anruf mit einem "O.K" und Kopiert danach die App Tasten zu den Funktionstasten gemäss der Modulkonfiguration.

# Konfiguration App-Favoriten Management

![4.png](/uploads/appfavoritemanagement/4.png)

> Der Client muss aktuell neu gestartet werden, damit die neuen Favoriten/Kategorien auftauchen.
{.is-warning}


## Beim Speichern / Übernehmen anwenden
Wendet die Einstellungen sofort an, statt Zeitgesteuert oder Self-Service

## Quellbenutzer
Der Benutzer, dessen Favoriten als Vorlage geltens sollen.

## Quell-App-Favoriten übertragen zu:
Definiert ob die Favoriten für alle Benutzer oder nur für eine Gruppe von Benutzern kopiert werden.

## Kategorienamen
Eine oder mehrere Kategorienamen, welche für den Kopiervorgang genommen werden.

![2.png](/uploads/appfavoritemanagement/2.png)

## Favoriten kopieren:
Definiert, ob nur eine gewisse Kategorie gemäss dessen Namen oder alle Favoriten's kopiert werden.

## Offset
Definiert den Offset der neuen Kategorien gegenüber bestehenden.
Z.b. wenn der User eine eigene Kategorie Pflegt, und ein Offset von 1 besteht, so wird die neue Kategorie unter der alten angelegt.

![5.png](/uploads/appfavoritemanagement/5.png)


## Telefon-Funktionstasten gemäss Einstellungen im anderen Tab updaten
Updatet auch die Telefon-Funktionstasten gemäss einstellungen im anderen Tab nachdem die Favoriten kopiert wurden.

# Telefon-Funktionstasten zu App-Favoriten
In diesem Modus werden die Telefon-Funktionstasten von einem Benutzer auf eine Gruppe, oder für jeden in der Gruppe die eigenen Tasten kopiert.

> Es werden nur Benutzertasten / Gruppentasten und Direktwahlen kopiert, da nur dieser Unterstützt werden.
{.is-danger}


![6.png](/uploads/appfavoritemanagement/6.png)

## Beim Speichern / Übernehmen anwenden
Wendet die Einstellungen sofort an, statt Zeitgesteuert oder Self-Service

## Quellbenutzer
Der Benutzer, dessen Favoriten als Vorlage geltens sollen.

## Modus
Hier wird festgelegt, welcher Modus ausgeführt wird.

### Funktionstasten von Quellbenutzer zu Favoriten für Zielgruppe/Alle
Es werden die Funktionstasten des Quellbenutzers genommen und in Favoriten gewandelt und zur Zielgruppe / auf alle STARFACE Benutzer (inklusive des Eigenen) Kopiert.

### Für jeden Benutzer seine eigenen Funktionstasten zu Favoriten wandeln.
Bei jedem Benutzer werden dessen Telefon-FK zu App-Favoriten gewandelt und ihm zur Verfügung gestellt

## Übertragen zu:
Definiert ob die Telefon-FK für alle Benutzer oder nur für eine Gruppe von Benutzern kopiert werden.

## Funktionstastenmapping
Hier wird definiert, welcher Funktionstastenbereich genommen wird, und wie die Kategorie dazu heissen soll.

Links wird der Kategorienamen festgelegt, und Rechts muss die Kategorieposition + der Tastenbereich festgelegt werden. Dort ist das Format **\[Position\],\[Tastenbereich\]**

Z.b. wenn als Position "2" festgelegt wird, so wird die Kategorie unter der ersten ggf. vom User gepflegten Kategorie hinzugefügt.

Wenn "1" genommen wird, wird die Kategorie zu oberst bei den Favoriten angezeigt.

### Funktionstastenbereich
Beim Bereich kann ein Von-Bis Bereich oder eine einzelne Taste eingegeben werden.
Also z.b. 0-10 oder einfach die Taste "5"

> Die erste Funktionstaste ist die Taste 0, nicht die Taste 1, also z.b. die ersten 10 Tasten wären 0-9, nicht 1-10
{.is-warning}


![7.png](/uploads/appfavoritemanagement/7.png)


# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung