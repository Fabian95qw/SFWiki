<!-- TITLE: Exchange Kalender Connector -->
# Beschreibung
Das Modul analysiert automatisch Kalendereinträge über die norminierte Schnittstelle vom Exchange-Server resp. Office 365 und setzt bei einem gefundenen Termineintrag den Chat-Status und den entsprechenden Text z.B. "13:00 - 15:15 Sitzung extern Muster AG" im UCC-Client. Die Abwesenheit kann zusätzlich als aktive Besetztanzeige auf den IP-Telefonen signalisiert werden. Die vorhandenen Kategorien im Outlook werden durch zusätzlich automatisch angelegte STARFACE-Kategorien ergänzt. So kann einfach die interne und externe Rufnummer auf eine Voicemail-Box oder auf eine Zielnummer umgeleitet werden. Die Zielnummern für die AUL-Funktion kann im Kalender-Eintrag einfach durch den Anwender definiert werden, z.B. mit der Zeichenfolge @extern: +41717271818. Ist die Sitzung vor dem definierten Zeitpunkt fertig, kann der Benutzer einfach aufeine definierte interne Nummer anrufen und die Einstellungen werden zurückgesetzt. 

Oder kurz Ausgedrückt:

* Abweseneit im Chat Setzen (Abwesend/DND/Offline)
* Indizierung der Telefontaste (Rot auf Apparaten Rot/Blau im UCC-Client/Webinterface)
* Setzen von Infos im Chatstatus
* Umleitungen/Voicemail intern/extern Aktivieren/Deaktivieren
* Extrahiert Nummernziele direkt aus dem Kalendertext mit @@Extern: @@Intern:

# Konfiguration
![1](/uploads/exchange-kalender-connector/1.png "1")
## CheckIntervall
### Timer
Hier definiert man den Intervall, in denen der Kalender überprüft wird.

### Exchange Gruppe
Das Modul wird nur auf alle Mitglieder dieser Gruppe angewendet.
Jeder User der Gruppe braucht eine Korrekt konfigurierte E-Mail Adresse, da das Modul den Status des Kalenders für diesen Benutzer überprüft.

## Funktionen bei Abwesenheit
### Funktionstastenindikator
Man kann Konfigurieren, ob die Funktionstasten bei Abwesenheit einen speziellen Status erhalten. 
**Bei der Option "Blau" werden die BLF's nur im UCC-Client Blau dargestellt! BLF's an den Telefonen sind dann Rot**

### Chatindikator
Wenn nun ein Kalendereintrag erreicht wird, erhält der Benutzer diesen Status im Chat.

### Statustext div.
Während eines Termins wird zusätlich zum Funktionasten- und Chatindikator, auch die Statusnachricht gesetzt.
Im Normall ist diese der Titel des Kalendereintrags im Exchange (Mit Ausnahme von Privaten Kalendereinträgen).

Mithilfe der Haken **Terminuhrzeit Von-Bis im Chatstatustext Anzeigen** 	erhält der Statustext vor dem Text noch ein Feld [Uhrzeit]
Die Uhrzeit lässt sich im "Simpledateformat" im Feld **Formatierung der Uhrzeit** konfigurieren.

## Alarme
Es gibt die Möglichkeit bei Problemen mit dem Exchange Connector, oder mit Umleitungszeieln eine E-Mail zu alamieren.

# Exchange-Verbindung

![2](/uploads/exchange-kalender-connector/2.png "2")


![3](/uploads/exchange-kalender-connector/3.png "3")

![4](/uploads/exchange-kalender-connector/4.png "4")

![5](/uploads/exchange-kalender-connector/5.gif "5")
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch:8018/lizenzierung
