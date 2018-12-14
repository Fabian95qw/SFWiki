<!-- TITLE: Eigene Sensoren Erstellen -->
# PRTG-Kern Komponenten Erklärung
Wenn das PRTG-Kernmodul installiert ist, stellt dieses zwei Funktionen zur Verfügung, mit welchen eigene Channels erstellt werden können.

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
* CustomUnit (STRING): Wenn die Unit auf "Custom" gestellt wurde, kann hier ganz einfach eine eigene Einheit angegeben werden.
* Addition Parameters (MAP<Elementname, Value>) erlaubt es weitere Parameter für den Channel zu setzen. Siehe dafür erneut: https://prtg.paessler.com/api.htm?username=demo&password=demodemo&tabid=7
		
### Outputs:
Keine

# Erstellung von Add-Ons für den PRTG-Kern
Hier wird Demonstrativ ein Modul gebaut, welches die eingehenden Anrufe zählt.

## Modul erstellen

### Eintrittspunkt Anruf
Wir erstellen ein neues Modul, und setzen den Modul Typ (**module-type**) auf erweitert (**Extended**), und wählen anschliessend einen Eintrittspunkt für Anrufverarbeitungen (**Call Processing Entrypoint**), mit dem Aktivierungstyp für Alle eingehenden Anrufe (**on all incoming calls**)

Damit haben wir nun ein Modul, welches einen Eintrittspunkt für alle Eingehenden Anrufe hat. 

![Tutorial 2](/uploads/prtg/tutorial-2.png "Tutorial 2")

### Code für Eintrittspunkt des Anrufs
Wir wenden die Funktionen GetVariable/SetVariable an, um bei jedem Anruf jeweils eine Zählervariable zu beziehen, und diese um 1 zu erhöhen.

![Tutorial 3](/uploads/prtg/tutorial-3.png "Tutorial 3")

### GUI-Design
Für den Eintrittspunkt der Sensor Aktualisierung Designen wir eine Kleine GUI, um Folgende Werte Konfigurieren zu können:

* Sensorname
* Chanellname
* Timer für Anzahl Aktualisierungen

### Eintrittspunkt für 

![Tutorial 4](/uploads/prtg/tutorial-4.png "Tutorial 4")

![Tutorial 5](/uploads/prtg/tutorial-5.png "Tutorial 5")

![Tutorial 6](/uploads/prtg/tutorial-6.png "Tutorial 6")

## Erklärung des Ablaufs