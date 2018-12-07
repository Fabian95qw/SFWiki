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

![2](/uploads/exchange-kalender-connector/2.png "2")

![3](/uploads/exchange-kalender-connector/3.png "3")

![4](/uploads/exchange-kalender-connector/4.png "4")

![5](/uploads/exchange-kalender-connector/5.gif "5")
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch:8018/lizenzierung
