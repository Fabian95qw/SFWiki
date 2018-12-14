<!-- TITLE: Eigene Sensoren Erstellen -->
# PRTG-Kern Komponenten Erklärung
Wenn das PRTG-Kernmodul installiert ist, stellt dieses einige Funktionen zur Verfügung, mit welchen eigene Channels erstellt werden können.

![Tutorial 1](/uploads/prtg/tutorial-1.png "Tutorial 1")

## GetPackage
Mithilfe des GetPackage Befehls kann ein bestimmter Sensor bezogen werden, zu dem man später den Channel hinzufügen will.

### Inputs:
* Sensorname (STRING): Der Sensor, welcher verwendet werden soll.

### Outputs:
* _Package (OBJECT): Das Paket, des Sensors

## AddResultToPackage

* Fügt dem Mithilfe von GetPackage geholtem Paket einem Channel des Sensors ein Resultat hinzu
* Wenn es den Channel auf dem PRTG-Server schon gibt, dann wird dort der neue Wert gesetzt.
* Wenn es den Channel noch nicht gibt, wird er automatisch erstellt.

### Inputs:
* Package (OBJECT): Das Paket das Mithilfe von GetPackage bezogen wurde.
* Channelname (STRING): Der Name des Channels, dem der neue Wert zugewiesen werden soll.
* Value (STRING): Der Wert, der dem Channel zugewiesen werden soll. Dieser wird als String verlangt, aber man kann auch Zahlen hinterlegen.
* Unit (STRING|DROPDOWN): Es gibt eine Verschiedene Anzahl vordefinierter Einheiten, auf dem PRTG-Monitor.:
    BytesBandwidth,
		BytesMemory,
		BytesDisk,
		Temperature,
		Percent,
		TimeResponse,
		TimeSeconds,
		Custom,
		Count,
		BytesFile,
		SpeedDisk,
		SpeedNet,
		TimeHours 
		Alle Infos dazu gibt es bei Paessler: https://prtg.paessler.com/api.htm?username=demo&password=demodemo&tabid=7
* CustomUnit (STRING): Wenn die Unit auf "Custom" gestellt wurde, kann hier ganz einfach ein
		
### Outputs:**
Keine

# Erstellung von Add-Ons für den PRTG-Kern
Das PRTG-Modul ist so gebaut, dass jeder seine eigenen Channels für die Starface Designen kann, hier wird Demonstrativ ein Modul gebaut, welches die eingehenden Anrufe zählt.