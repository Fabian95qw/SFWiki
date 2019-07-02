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

## Templatedefinition
## 
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch:8018/lizenzierung
