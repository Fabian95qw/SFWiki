<!-- TITLE: PRTG Monitor -->
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

Der Source-Code der Sensoren findet man hier: https://github.com/Fabian95qw/PRTG-2-Starface/tree/master/src/server/nucom/module/prtg
Die Vorkompillierten SFM-Dateien findet man hier: https://github.com/Fabian95qw/PRTG-2-Starface/tree/master/bin/server

### Sensoren
Für die Individuellen Sensoren gibt es eigene Artikel:

PRTG Sensor: Anlagenverbund On-/Offline: WIP
PRTG Sensor: Anzahl Gruppenmitglieder: WIP
PRTG Sensor: CPU Verbrauch: WIP
PRTG Sensor: Freier Speicherplatz: WIP
PRTG Sensor: Leitungen On-/Offline: WIP
PRTG Sensor: RAM Verbrauch: WIP
PRTG Sensor: Telefone On-/Offline: WIP
PRTG Sensor: Anzahl ungenutzer Lizenzen:WIP

## Erstellung eigener Add-Ons
Hierfür wurde ein eigener Artikel erfasst: WIP
# Konfiguration PRTG-Monitor Server
## Installieren des Sensors
Um den Sensor auf dem PRTG-Monitor Verfügbar zu machen, muss man ihn zuerst Runterladen (oder selbst Kompilieren), und anschliessend im "EXEXML" Verzeichnis des PRTG-Monitors Platzieren.

**Wichtig! Auf dem Server muss Java installiert sein!**

Standardpfad: "C:\Programme(x86)\PRTG Network Monitor\Custom Sensors\EXEXML
Vorkompilliertes Installationspaket: https://github.com/Fabian95qw/PRTG-2-Starface/raw/master/bin/client/PRTGClient.jar (muss noch entpackt werden)

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
Dazu kann man folgenden Befehl ausführen:

> java -jar "C:\Program Files (x86)\PRTG Network Monitor\Custom Sensors\EXEXML\PRTGClient.jar" -h testface.nucom.ch -t 123:1ebe2e9249d866e6d9ccea5456cdf7ddbf09aafd8859bf3a75b89051870b37362f8ea26cdece9d87a0cf57909482062949c2353df920a49ba6ba85437f1066e4 -s Festplatten -i PRTG-Kern -d **true**

Je nachdem, wo das Problem ist, erhält man ein anderes Ergebnis.

### Java wurde nicht gefunden
Entweder ist Java nicht installiert, oder nicht korrekt in der Systemungebungsvariable hinterlegt. 

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch/lizenzierung
