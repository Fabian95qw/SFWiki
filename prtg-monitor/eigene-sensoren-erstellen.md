<!-- TITLE: Eigene Sensoren erstellen -->
# PRTG-Kern Komponenten Erklärung
Wenn das PRTG-Kernmodul installiert ist, stellt dieses eine Funktion zur Verfügung, mit welcher eigene Channels erstellt werden können.

![Tutorial 1](/uploads/prtg-tutorial/tutorial-1.png "Tutorial 1")

## AddSensorData

* Fügt einem Sensor einen Channel hinzu, oder updatet diesen.
* Wenn dieser Sensor in der STARFACE noch nicht exisitert, wird er erstellt.

### Inputs:
* Sensorname (STRING): Der Name des Sensors, der Verwendet werden soll
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

![Tutorial 2](/uploads/prtg-tutorial/tutorial-2.png "Tutorial 2")

### Code für Eintrittspunkt des Anrufs
Wir wenden die Funktionen GetVariable/SetVariable an, um bei jedem Anruf jeweils eine Zählervariable zu beziehen, und diese um 1 zu erhöhen.

![Tutorial 3](/uploads/prtg-tutorial/tutorial-3.png "Tutorial 3")


