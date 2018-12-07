<!-- TITLE: Quelle: Datei Importer -->
# Beschreibung
Hier geht es Spezifisch um die Konfiguration des Datei-Importers im Adressbuch Importer
# Konfiguration
## Import
![Datei Import 1](/uploads/adressbuch-importer/datei-import-1.png "Datei Import 1")
### Protkoll

Hier muss im Voraus das Protokoll festgelegt werden, dessen Konfiguration verwendet werden soll.

### Fileimportmodus

**Nur spezifisches CSV Importieren**
In diesem Modus wird nur ein Spezifisches CSV in dem in der Konfiguration angegebenen Pfad gesucht. Dieser muss weiter unten bei „Spezifischer Dateiname“ angegeben werden.

**Alle CSV’s Importieren**
Die Starface lädt alle Dateien mit der Endung .csv aus dem Ordner herunter. Und Importiert diese nacheinander.

**Neuste CSV Importieren**
Er lädt die neuste Datei mit der Endung .CSV herunter. Hierbei überprüft er den Wert der letzten Änderung (Siehe Artikel „Wikipedia Changed Date“)

**Spezifischer Dateiname**
Wird nur beim Fileimportmodus „Nur Spezifisches CSV Importieren“ benötigt. Dieser Dateiname wird hinten an den Konfigurierten FTP/SMB Pfad angehängt.

**Ignoriere erste Zeile**
Ignoriert die erste Zeile der CSV’s. Dies wird Z.B. benötigt, wenn die Spaltenbeschriftungen noch vorhanden sind. 
Template für Importdateien
Beim Export der Adressen aus anderen Programmen sind diese nicht unbedingt gerade Starface Konform Formatiert, deshalb kann man ein eigenes Template für eigene Imports einspielen.
 
 **Eigenes Template verwenden**
Das eigene Template für den Import verwenden. Wenn dieses hochgeladen wurde
  
**Beispiel Template**
Beispieldaten aus Applikation XY
![Vorlageappxy](/uploads/adressbuch-importer/vorlageappxy.png "Vorlageappxy")


KdNr	Name	Vorname	Abteilung	Firma	PLZ	Strasse	Admin	Telnr
1337	Mustermann	Max	Elektronik	Musterfirma AG	1234	Musterstrasse 23	false	+41 234 56 78
2354	Musterfrau	Maria	Intern		5343	Malerstrasse	True	+41 576 83 23
Diese sollen in die Starface Importiert werden. Hierfür kann ein Template generiert werden.
Als Vorlage für das Template benutzen wir die Excel CSV Vorlage der Starface (Adressbuch  Importieren  Excel-Vorlage für CSV-Datei  Herunterladen
Die darin enthaltenen Spaltennamen werden von der Starface erkannt.
Teile der Starface Vorlage
Vorname [contact:firstname]	Name [contact:familyname]	Firma[contact:company]
Template mithilfe der Starface Vorlage & den Beispieldaten erstellen
KdNr	Name	Vorname	Abteilung	Firma	PLZ	Strasse	Admin	Telnr
1337	Mustermann	Max	Elektronik	Musterfirma AG	1234	Musterstrasse 23	false	+41 234 56 78
2354	Musterfrau	Maria	Intern		5343	Malerstrasse	True	+41 576 83 23
Resultierendes Template:
(LEER)	Name [contact:familyname]	Vorname [contact:firstname]	(LEER)	Firma [contact:company]	PLZ [address:postcode]	Straße [address:street]	(LEER)	Rufnummer [telephone:phone]
Das Resultierende Template muss im CSV Format Semicolon (;) getrennt & im UTF-8 Format abgespeichert werden.
In diesem Fall würde der „rohe“ CSV-Code so aussehen:
[LEER];Name [contact:familyname];Vorname [contact:firstname];;Firma [contact:company];PLZ [address:postcode];Straße [address:street];;Rufnummer [telephone:phone]
Dies kann so in den Menüpunkt „Eigenes Template“ hochgeladen werden. Somit verwendet diese Modulinstanz beim Import dieses Template, um die Kontakte korrekt zu interpretieren.
 
 
http(s) Get
 
Die http(s) get Funktion erlaubt es eine CSV. Von einem Webhost abzurufen. 
Request Ergebnis
Das Request Ergebnis gibt das Ergebnis des letzten http(s) Requests zurück. Also Z.b. 404 not found.
FTP-Konfiguration
Hier wird die FTP Verbindung Konfiguriert. 
FTP Status

Dieses Feld gibt Feedback, ob die aktuelle Konfiguration in Ordnung ist. Dieser Wert wird beim Abspeichern des Moduls vom System überschrieben.
FTP Import Pfad

Dies ist der Import Pfad zum Adressbuch. Er muss mit einem Backslash („\“) beginnen und im letzten Ordner ohne Backslash aufhören. Ein Dateiname darf nicht angehängt werden. (SIEHE Import)
 
SMB-Konfiguration
SMB Status
Dieses Feld gibt Feedback, ob die aktuelle Konfiguration in Ordnung ist. Dieser Wert wird beim Abspeichern des Moduls vom System überschrieben.
Import Dateipfad

Dies ist der Import Pfad zum Adressbuch. Er muss mit einem Slash („/“) beginnen und im letzten Ordner ohne Slash aufhören. Ein Dateiname darf nicht angehängt werden. (SIEHE Import)

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch:8018/lizenzierung
