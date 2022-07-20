---
title: PRTG-Monitor 7.X
description: 
published: true
date: 2022-07-20T08:09:26.581Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:58:36.781Z
---

# Beschreibung
Dies ist das Kernmodul vom PRTG-Monitoring Modul für die Starface
# Open-Source!
Dieses Modul ist als Open-Source auf Github Verfügbar: https://github.com/Fabian95qw/PRTG-2-Starface

Source: https://github.com/Fabian95qw/PRTG-2-Starface/tree/master/src
Pre-Compiled: https://github.com/Fabian95qw/PRTG-2-Starface/tree/master/bin

# Konfiguration Starface Module & Sensoren
## Kernmodul Konfigurieren
Bevor man irgendwelche Sensoren definiert, muss man auf der Starface das Kernmodul installieren.
Die vorkompillierte SFM-Datei findet man im Verzeichnis: https://github.com/Fabian95qw/PRTG-2-Starface/tree/master/bin/server
Vom Kern muss eine Instanz angelegt werden. Der Name der Instanz wird später im PRTG-Monitor benötigt.

## Installation von Sensoren
### Downloads

Der Source-Code der Sensoren findet man hier: https://github.com/Fabian95qw/PRTG-2-Starface/tree/master/src/server/si/module/prtg
Die Vorkompillierten SFM-Dateien findet man hier: https://github.com/Fabian95qw/PRTG-2-Starface/tree/master/bin/server
 
### Sensoren
Für die Individuellen Sensoren gibt es eigene Artikel:

PRTG Sensor: Anlagenverbund On-/Offline: http://wiki.si-solutions.ch/prtg-monitor/sensor-anlagenverbund-on-offline
PRTG Sensor: Anzahl Gruppenmitglieder: http://wiki.si-solutions.ch/prtg-monitor/sensor-anzahl-gruppenmitglieder
PRTG Sensor: CPU Verbrauch: http://wiki.si-solutions.ch/prtg-monitor/sensor-cpu-verbrauch
PRTG Sensor: Freier Speicherplatz: http://wiki.si-solutions.ch/prtg-monitor/sensor-freier-speicherplatz
PRTG Sensor: Leitungen On-/Offline: http://wiki.si-solutions.ch/prtg-monitor/sensor-leitungen-on-offline
PRTG Sensor: RAM Verbrauch: http://wiki.si-solutions.ch/prtg-monitor/sensor-ram-verbrauch
PRTG Sensor: Telefone On-/Offline: http://wiki.si-solutions.ch/prtg-monitor/sensor-telefone-on-offline
PRTG Sensor: Anzahl ungenutzer Lizenzen: http://wiki.si-solutions.ch/prtg-monitor/sensor-ungenutzte-lizenzen

## Erstellung eigener Add-Ons
Hierfür wurde ein eigener Artikel erfasst: http://wiki.si-solutions.ch/prtg-monitor/eigene-sensoren-erstellen
# Konfiguration PRTG-Monitor Server
## Installieren des Sensors
Um den Sensor auf dem PRTG-Monitor Verfügbar zu machen, muss man ihn zuerst Runterladen (oder selbst Kompilieren), und anschliessend im "EXEXML" Verzeichnis des PRTG-Monitors Platzieren.

> Wichtig! Auf dem Server muss Java installiert sein!
{.is-warning}


Standardpfad: "C:\Programme(x86)\PRTG Network Monitor\Custom Sensors\EXEXML
Vorkompilliertes Installationspaket: https://github.com/Fabian95qw/PRTG-2-Starface/raw/master/bin/client/PRTGClient.rar (muss noch entpackt werden)

![Install](/uploads/prtg/install.png "Install")

## Konfiguration des Sensors
**Man muss das Kernmodul, sowie die entsprechenden Sensoren bereits Konfiguriert haben**
Wenn die .bat Korrekt platziert wurde, müsste diese nun in den Sensoren unter "Programm/Skript erweitert" zur Verfügung stehen.
Zur erstellung der Parameter kann die Create-Sensorstring.bat ausgeführt werden.
Dann sollt sich ein entsprechendes Fenster zur Erstellung der Parameter öffnen.
Man muss den Namen des Kernmoduls, einen STARFACE Login & Passwort, sowie den Sensornamen, den man Abrufen will hinterlegen.

![create-sensorstring](/uploads/prtg/create-sensorstring.png "create-sensorstring")

Wenn alles korrekt eingegeben wurde, und man auf "Testen" geht, sollte ein entsprechender Sensorstring generiert werden.
Beispiel: -h %host -t 123:1ebe2e9249d866e6d9ccea5456cdf7ddbf09aafd8859bf3a75b89051870b37362f8ea26cdece9d87a0cf57909482062949c2353df920a49ba6ba85437f1066e4 -s Festplatten -i PRTG-Kern -d false

-h %host  ==> %host wird vom PRTG-Monitor durch den Hostnamen/IP des Gerätes ersetzt. **Bitte nicht anpassen**
-t [Token]  ==> Der generierte Token aus Benutzernamen und Passwort **Bitte nicht anpassen**
-s [Sensorname] ==> Der Sensorname, der Abgerufen werden soll. Diesen kann für mehrere Sensoren einfach editiert werden
-i [PRTG-Kern-Name] ==> Der Name der Instanz des Kernmoduls. Muss nur angepasst werden, falls man dieses Umbenennt.
-d true/false ==> Debugging. Ist standardmässig auf False. **Wenn dieses auf true gesetzt wird, erzeugt der Sensor logs. Gleichzeitig liefert er aber keine Resultate mehr ans PRTG-System zurück**

![create-sensor](/uploads/prtg/create-sensor.gif "create-sensor")
# Es funktioniert nicht!
Letzten gab es mehrere Probleme, mit Personen bei denen der PRTG-Monitor nicht korrekt funktioniert hat.
Hier sind noch einige Hilfestellungen dazu.

## XML: Das zurückgelieferte XML entspricht nicht dem erwarteten Schema. (Code: PE233) -- JSON: Das zurückgelieferte JSON entspricht nicht der erwarteten Struktur (Invalid JSON.). (Code: PE231)
Dieser Fehler wird von Seitens PRTG-Generiert, wenn der Sensor kein gültiges XML vom Client Sensor erhält.

Um dies zu beheben, können wir Clientseitiges Debugging verwenden.

Die PRTGClient.jar kann von Hand im CMD ausführen, um so fehlermeldungen zu finden.
Dazu kann man den Folgenden Befehl, mit dem generierten Sensorstring ausführen: 

> java -jar "C:\Program Files (x86)\PRTG Network Monitor\Custom Sensors\EXEXML\PRTGClient.jar" -h testface.si-solutions.ch -t 123:1ebe2e9249d866e6d9ccea5456cdf7ddbf09aafd8859bf3a75b89051870b37362f8ea26cdece9d87a0cf57909482062949c2353df920a49ba6ba85437f1066e4 -s Festplatten -i PRTG-Kern -d **true**

Je nachdem, wo das Problem ist, erhält man ein anderes Ergebnis.

### PRTG Monitor Sensor Debug-Log
Wenn beim Manuellen Test alles zu klappen scheint, kann man für einzelne Sensoren im PRTG-Monitor die Ergebnisse auf die Festplatte schreiben lassen. So können weitere Fehlerquellen ermittelt werden.

Zur aktivierung der Ausgabe müssen sie bei "Umgang mit dem Ergebnis" den Wert auf "Ergebnis Speichern" ändern.

![activate-output](/uploads/prtg/activate-output.png "activate-output")

Nach einem Ausgeführten check sollten im Verzeichnis C:\ProgramData\Paessler\PRTG Network Monitor\Logs\sensors zwei Dateien welche mit Sensor \[Nummer\] beginnen, vorhanden sein.
Diese enthalten das Ergebnis der Abfrage.

### Fehler: Der Befehl "pushd" ist entweder falsch geschrieben oder konnte nicht gefunden werden
Je Betriebssystem, und Rechten kann es sein, dass pushd als Befehl im Umfeld nicht verfügbar ist.
Pushd sollte das Verzeichnis auf das Verzeichnis ändern, in dem die .bat Datei liegt.

Wird dies nicht gemacht, kommt danach der Folgefehler: "Error: Unable to access jarfile PRTGClient.jar", da die Batch Datei nicht im korrekten Pfad ist.

Der einfache weg hierbei ist es, den Absoluten Pfad in die STARFACE.bat zu schreiben:
`java -jar C:\Program Files (x86)\PRTG Network Monitor\Custom Sensors\EXEXML\PRTGClient.jar %*`

### Der Befehl "java" ist entweder falsch geschrieben oder konnte nicht gefunden werden.
Dies Tritt auf, wenn java nicht installiert ist, oder der PRTG Service kein Zugriff auf die JAVA_HOME Variable hat.
In diesem Fall muss im Starface.bat file der Pfad zur java.exe vollständig eingetragen werden, oder
vorab ein cd ins Verzeichnis der Java Datei vorgenommen werden.

Z.b. so: 
`cd "C:\Program Files\Java\jre1.8.0_333\bin"
java.exe -jar "C:\Program Files (x86)\PRTG Network Monitor\Custom Sensors\EXEXML\PRTGClient.jar" %*
`
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung
