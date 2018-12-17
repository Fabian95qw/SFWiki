<!-- TITLE: PRTG Monitor -->
# Beschreibung
# Open-Source!
Dieses Modul ist als Open-Source auf Github Verfügbar: https://github.com/Fabian95qw/PRTG-2-Starface

Source: https://github.com/Fabian95qw/PRTG-2-Starface/tree/master/src
Pre-Compiled: https://github.com/Fabian95qw/PRTG-2-Starface/tree/master/bin

# Konfiguration Starface Module & Sensoren
## Kernmodul Konfigurieren
Bevor man irgendwelche Sensoren definiert, muss man auf der Starface das Kernmodul installieren.
Die vorkompillierte SFM-Datei findet man im Verzeichnis: https://github.com/Fabian95qw/PRTG-2-Starface/tree/master/bin/server/Core

![Core](/uploads/prtg/core.png "Core")

### Port öffnen
Da das Modul Open-Source ist, werden im Modul keine Root-Scripts Verfügbar gemacht.
Das beduetet wiederum, dass man zuerst mit Root-Rechten den Port, welchen man im PRTG-Kern definiert hat öffnen muss.

Befehle zum öffnen des Ports:

```text
iptables -I INPUT 3 -p tcp -m tcp --dport [PORT] -j ACCEPT
service iptables save
```

**Wichtig! Bei einem Update der Starface muss der Port erneut geöffnet werden**

## Installation von Demo-Add-Ons
### Downloads

Der Source-Code der Demopakete findet man hier: https://github.com/Fabian95qw/PRTG-2-Starface/tree/master/src/server/nucom/module/prtg/sensors
Die Vorkompillierten SFM-Dateien findet man hier: https://github.com/Fabian95qw/PRTG-2-Starface/tree/master/bin/server/DemoSensors

### Demopakete
Für die Individuellen Demopakete gibt es eigene Artikel:

PRTG Demo: Anlagenverbund On-/Offline 	
PRTG Demo: Anzahl Gruppenmitglieder 	
PRTG Demo: CPU Verbrauch 	
PRTG Demo: Freier Speicherplatz 	
PRTG Demo: Leitungen On-/Offline 	
PRTG Demo: RAM Verbrauch 	
PRTG Demo: Telefone On-/Offline 	
PRTG Demo: Anzahl ungenutzer Lizenzen 	

## Erstellung eigener Add-Ons
Hierfür wurde ein eigener Artikel erfasst: http://wiki.nucom.ch:8018/prtg-monitor/eigene-sensoren-erstellen
# Konfiguration PRTG-Monitor Server
## Installieren des Sensors
Um den Sensor auf dem PRTG-Monitor Verfügbar zu machen, muss man ihn zuerst Runterladen (oder selbst Kompilieren), und anschliessend im "EXEXML" Verzeichnis des PRTG-Monitors Platzieren.

Standardpfad: "C:\Programme(x86)\PRTG Network Monitor\Custom Sensors\EXEXML
Vorkompilliertes Installationspaket: https://github.com/Fabian95qw/PRTG-2-Starface/raw/master/bin/client/Client.rar (muss noch entpackt werden)

![Install](/uploads/prtg/install.png "Install")

## Konfiguration des Sensors
Wenn die .bat Korrekt platziert wurde, müsste diese nun in den Sensoren unter "Programm/Skript erweitert" zur Verfügung stehen.
Bei der erstellung müssen die Parameter wie folgt angegeben werden: 

%host [PORT] [PASSWORT] [SENSORNAME] [TRUSTALLCA] [LOGLOCATION]

* %host ==> Ist ein Parameter vom PRTG-System, es entspricht der IP-Adresse des Geräts
* PORT ==> Der Port, der im PRTG-Modul auf der Starface definiert wurde.
* SENSORNAME ==> Der Name des Sensors, der von der Starface abgerufen werden soll. 
* TRUSTALLCA ==> Vertraut auch Zertifikaten, welcher nicht von einer Offiziellen Stelle kommen. Das Modul verwendet das gleiche Zertifikat für den Verschlüsselten verkehr, wie der Tomcat Server (Starface Webinterface)
* LOGLOCATION ==> Der Sensor enthält einen minimalistischen Logger, falls mal etwas gar nicht klappt, kann man hier eine Loglocation angeben.

![Prtgdemosensor](/uploads/prtg/prtgdemosensor.gif "Prtgdemosensor")

## Success Channel
Mit jedem Sensor kommt automatisch der Success-Channel. Dieser Channel sagt, ob das Passwort beim Login korrekt war.
1 == O.K
0 == Passwort falsch.
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch:8018/lizenzierung
