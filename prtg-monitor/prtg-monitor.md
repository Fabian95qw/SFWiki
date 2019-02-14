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

PRTG Demo: Anlagenverbund On-/Offline: http://wiki.nucom.ch:8018/prtg-monitor/demo-anlagenverbund-on-offline
PRTG Demo: Anzahl Gruppenmitglieder: http://wiki.nucom.ch:8018/prtg-monitor/demo-anzahl-gruppenmitglieder	
PRTG Demo: CPU Verbrauch: http://wiki.nucom.ch:8018/prtg-monitor/demo-cpu-verbrauch	
PRTG Demo: Freier Speicherplatz: http://wiki.nucom.ch:8018/prtg-monitor/demo-freier-speicherplatz
PRTG Demo: Leitungen On-/Offline: http://wiki.nucom.ch:8018/prtg-monitor/demo-leitungen-on-offline
PRTG Demo: RAM Verbrauch: http://wiki.nucom.ch:8018/prtg-monitor/demo-ram-verbrauch
PRTG Demo: Telefone On-/Offline: http://wiki.nucom.ch:8018/prtg-monitor/demo-telefone-on-offline
PRTG Demo: Anzahl ungenutzer Lizenzen: http://wiki.nucom.ch:8018/prtg-monitor/demo-ungenutzte-lizenzen

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

%host [PORT] [PASSWORT] [SENSORNAME] [TRUSTALLCA] [DEBUG]

* %host ==> Ist ein Parameter vom PRTG-System, es entspricht der IP-Adresse des Geräts. **Dieser muss genau so eingetragen werden! Nicht durch %192.168.XXX.XXX ersetzen!**
* PORT ==> Der Port, der im PRTG-Modul auf der Starface definiert wurde.
* SENSORNAME ==> Der Name des Sensors, der von der Starface abgerufen werden soll. 
* TRUSTALLCA (Boolean true/false)==> Vertraut auch Zertifikaten, welcher nicht von einer Offiziellen Stelle kommen. Das Modul verwendet das gleiche Zertifikat für den Verschlüsselten verkehr, wie der Tomcat Server (Starface Webinterface)
* DEBUG (Boolean true/false) ==> Der Sensor enthält eine Logging funktion, zum finden von Fehlern. **Warnung! Aktivieren des Debug Logs führt automatisch zu fehlermeldungen im PRTG-Monitor, gibt dafür allerlei Logs aus.**

![Prtgdemosensor](/uploads/prtg/prtgdemosensor.gif "Prtgdemosensor")

```text
Wichtig! Auf dem Server muss Java installiert sein!
```

## Success Channel
Mit jedem Sensor kommt automatisch der Success-Channel. Dieser Channel sagt, ob das Passwort beim Login korrekt war.
1 == O.K
0 == Passwort falsch.

# Es funktioniert nicht!
Letzten gab es mehrere Probleme, mit Personen bei denen der PRTG-Monitor nicht korrekt funktioniert hat.
Hier sind noch einige Hilfestellungen dazu.

## XML: Das zurückgelieferte XML entspricht nicht dem erwarteten Schema. (Code: PE233) -- JSON: Das zurückgelieferte JSON entspricht nicht der erwarteten Struktur (Invalid JSON.). (Code: PE231)
Dieser Fehler wird von Seitens PRTG-Generiert, wenn der Sensor kein gültiges XML vom Client Sensor erhält.

Um dies zu beheben, können wir Clientseitiges Debugging verwenden.

Die PRTGClient.jar kann von Hand im CMD ausführen, um so fehlermeldungen zu finden.
Dazu kann man folgenden Befehl ausführen:

> java -jar "C:\Program Files (x86)\PRTG Network Monitor\Custom Sensors\EXEXML\PRTGClient.jar" XXX.XXX.XXX.XXX Port Passwort Demosensor true true

Je nachdem, wo das Problem ist, erhält man ein anderes Ergebnis.

### Java wurde nicht gefunden
Entweder ist Java nicht installiert, oder nicht korrekt in der Systemungebungsvariable hinterlegt.

### java.net.SocketException: Connection reset
Es konnte keine Verbindung zum PRTG-Sensor auf der Starface hergestellt werden. Entweder ist der PORT nicht geöffnet, oder der PRTG-Monitor Dienst auf der Starface ist nicht in Betrieb.

### Connection Failed.
Das ist eine fortlaufende Fehlermeldung, die während der Verarbeitung des Modul auftritt.

>  java -jar "C:\Program Files (x86)\PRTG Network Monitor\Custom Sensors\EXEXML\PRTGClient.jar" 192.168.123.123 25590 Passwort Demosensor true true
>  [EntryPoint] Opeing Connection to: 192.168.123.123 on Port: 25590
>  [Connection] Encrypting Password
>  [Connection] Starting Handshake
>  [Connection]HandShake Completed
>  [Connection]Writing Password
>  [Connection] Writing Sensor to Access
>  [Connection]Waiting for Server Response
>  [Connection] Connection Failed.
>  [Connection]java.net.SocketException: Connection reset
>  at java.net.SocketInputStream.read(Unknown Source)
>  at java.net.SocketInputStream.read(Unknown Source)
>  at sun.security.ssl.InputRecord.readFully(Unknown Source)
>  at sun.security.ssl.InputRecord.read(Unknown Source)
>  at sun.security.ssl.SSLSocketImpl.readRecord(Unknown Source)
>  at sun.security.ssl.SSLSocketImpl.readDataRecord(Unkn own Source)
>  at sun.security.ssl.AppInputStream.read(Unknown Source)
>  at sun.nio.cs.StreamDecoder.readBytes(Unknown Source)
>  at sun.nio.cs.StreamDecoder.implRead(Unknown Source)
>  at sun.nio.cs.StreamDecoder.read(Unknown Source)
>  at java.io.InputStreamReader.read(Unknown Source)
>  at java.io.BufferedReader.fill(Unknown Source)
>  at java.io.BufferedReader.readLine(Unknown Source)
>  at java.io.BufferedReader.readLine(Unknown Source)
>  at nucom.module.prtg.client.connection.Connection.Ope n(Connection.java:1
>  30)
>  at nucom.module.prtg.client.EntryPoint.main(EntryPoin t.java:58)

Dies deutet darauf hin, dass das Modul Probleme mit Verarbeitung der Sensordaten hat.

### javax.net.ssl.SSLHandshakeException
Die Serververbindung wurde aufgrund eines Problems mit dem SSL-Handshake unterbrochen. Dies kann u.a. passieren, wenn ein Selbstsigniertes Zertifikat verwendet wurde, ohne den entsprechenden **TRUSTALLCA** Parameter auf **True** zu setzen

## Der Sensor enthält nur einen Success Channel
Wenn man vom Server einen Sensor verlangt, welcher gar nie existiert, gibt dieser Trotzdem einen Success Channel zurück, da dieser eine Aussage, über den Loginstatus macht. (0==Passwort falsch, 1==Eingeloggt)
Falls der Channel 0 ist, sollte man das Passwort nochmals überprüfen.

Falls der Sensor nach wie vor nur einen Channel hat, sollte man prüfen, ob Sensorname auf dem Server, sowie Client übereinstimmen, und das Servermodul auch eine korrekte Zeit zur aktualisierung der Daten hat.
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch:8018/lizenzierung
