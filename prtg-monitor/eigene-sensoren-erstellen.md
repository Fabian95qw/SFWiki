<!-- TITLE: Eigene Sensoren Erstellen -->

# Erstellung von Add-Ons für den PRTG-Kern
Das PRTG-Modul ist so gebaut, dass jeder seine eigenen Channels für die Starface Designen kann, hier wird Demonstrativ ein Modul gebaut, welches die eingehenden Anrufe zählt.
## PRTG-Kern Komponenten Erklärung
Wenn das PRTG-Kernmodul installiert ist, stellt dieses einige Funktionen zur Verfügung, mit welchen eigene Channels erstellt werden.

![Tutorial 1](/uploads/prtg/tutorial-1.png "Tutorial 1")

### GetPackage
Mithilfe des GetPackage Befehls kann ein bestimmter Sensor bezogen werden, zu dem man später den Channel hinzufügen will.

**Inputs:**
Sensorname (STRING): Der Sensor, welcher verwendet werden soll.

**Outputs:**
_Package (OBJECT): Das Paket, des Sensors

### AddResultToPackage
Fügt dem Mithilfe von GetPackage geholtem Paket einen Channel hinzu

**Inputs:**

**Outputs:**
.
