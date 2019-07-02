<!-- TITLE: User-Importer -->
# Beschreibung
Die Möglichkeit per CSV Userinformamationen für Anlagenbenutzer zu importieren
# Konfiguration
## Automatisierung

Hier können die allgemeinen Einstellungen für das Modul festgelegt werden.

![Automatisierung](/uploads/userimporter/automatisierung.jpg "Automatisierung")

### Importtimer
Die Userdaten können mithilfe des Timers regelmässig Synchronisiert werden.

### Account für Automatisierung

Der Account, welcher für die Anpassung der Namen angewendet werden muss.

```diff
- WICHTIG Der User muss ein Admin sein, sonst schlägt der Vorgang fehl!
```

```diff
- WICHTIG Das Adressbuch "users" muss aktivierte Schreibrechte haben
```

### Automatisierung beim Speichern anwenden
Wendet die aktuelle Konfiguration unabhängig vom Import-Timer sofort an. 
Wird vor allem zu Testzwecken benötigt.

### E-Mail Einstellungen
 
Hierbei handelt es sich um die E-Mail-Adresse des Benutzers, welcher alle nachfolgenden Fehlermeldungen erhalten soll.

### Alarme
**Alarm bei Fehlerhaftem Dateidownload**
Löst einen Alarm aus, wenn der Dateidownload vom FTP oder SMB Server fehlschlägt.

**Alarm, wenn das Leeren des Adressbuchs fehlschlägt**
Löst einen Alarm aus, wenn das Leeren des Adressbuchs fehlschlägt. Dieser Fehler tritt nur auf, wenn ein Ungültiges Zieladressbuch oder ein Adressbuch ohne Schreibrechte aufgerufen wird.

Wird nur benötigt, wenn das Adressbuchmanagement auf „Adressbuch leeren“ steht. 

**Import von 0 Kontakten als Alarm behandeln**
Wenn ein Export aus einer anderen Software fehlerhaft war, die CSV für den Download jedoch existiert, und von der Starface heruntergeladen wurde, schlägt diese Alarm, da keine Kontakte im File gefunden werden konnten 
(Vorsicht mit Header Zeile, wenn „Erste Zeile Ignorieren nicht gesetzt ist!)

## Nummernfilter
Wenn Nummern aus Fremdprogrammen importiert werden, welche nicht Starface Konform (Internationales Nummernformat) sind, können diese mithilfe des Nummernfilter korrigiert werden.
Der Nummernfilter erlaubt es, gewisse Nummernteile durch andere zu ersetzen.
Es wird immer nur das erste Vorkommen des Nummernteils ersetzt.
Zb: NummernTeil: 071 == Ersetzen durch: +41(71)
Nummer: 0715736071 wird zu +41(71)5736071

![Nummernfilter](/uploads/adressbuch-importer/nummernfilter.png "Nummernfilter")

### Regex
Der Nummernfilter unterstützt Regex. **Diese müssen immer mit REGEX: beginnen!**

**Beispiel**

Der REGEX : *^(\+41)\(?0?([0-9]{2})\)?* auf Nummern Angewendet:

Ursprüngliche Nummer	                    Nummer nach Regex
+41712345678	                                  +41712345678
+410712345678		              	               +41712345678
+41(71)2345678		              	              +41712345678
+41(071)2345678		                 	           +41712345678

Zum editieren von Regex sollte ein Hilfsprogramm wie z.b. Regex101 Verwendet werden.

Regex101 Beispiele:

* Einfacher Schweizer Nummernfilter: https://regex101.com/r/kV3vW4/1
* Komplexer Regex für das Filtern von allen +4[0-9] Nummern, inkl. Filterung von Klammern, Abständen, sowie Bindestrichen: https://regex101.com/r/Yb6MUI/1

## Template für Import definieren
Um die zu importierenden Daten einem User zuordnen zu können, muss ein entsprechendes Template designt werden.

### Beispiel Template

**Beispieldaten aus Applikation XY**

![Customtemplate](/uploads/userimporter/customtemplate.jpg "Customtemplate")

Diese sollen in die Starface Importiert werden. Hierfür kann ein Template generiert werden.
Als Vorlage für das Template benutzen wir die CSV-Import Vorlage der Starface:

![Template](/uploads/adressbuch-importer/template.png "Template")

Die darin enthaltenen Spaltennamen werden von der Starface erkannt.

Wir platzieren nun die Header in den Spalten, die den entsprechenden Spalten im ApplikationXY.csv Entsprechen:

```diff
- WICHTIG Die Spalte "comment" ist für die LoginID reserviert und muss ZWINGEND vorhanden sein.
```

![Templatecolored](/uploads/userimporter/templatecolored.jpg "Templatecolored")

**Das Resultierende Template muss im CSV Format Semicolon ( ; ) getrennt & im UTF-8 Format abgespeichert werden.**

In diesem Fall würde der „rohe“ CSV-Code so aussehen:

> First name [contact:firstname];Last name [contact:familyname];Company [contact:company];Academic title [contact:academic_title];Job title [contact:job_tilte];Street [address:street];ZIP code [address:postcode];City [address:city];State [address:state];Phone number [telephone:phone];[LEER];[LEER];[LEER];E-mail [email:e-mail];URL [email:url];LoginID[module:comment]


Dies kann so in den Menüpunkt „Eigenes Template“ hochgeladen werden. Somit verwendet diese Modulinstanz beim Import dieses Template, um die Daten korrekt zu interpretieren.

# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch:8018/lizenzierung
