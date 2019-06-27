<!-- TITLE: MOH Livestream Helper -->
# Beschreibung
Ein Gratistool welches auf der Starface MPG123 installiert, damit Livestreams als Warteschlangenmusik hinterlegt werden können.

**WARNUNG**
Das Tool kann nicht mehr entfernt werden, und es könnte zu komplikationen bei Updates kommen

**Gratislizenz: 2VSXC-TDY4K-7SHXG-4RF7W-F7NT7**
# Konfiguration
## Erstinstallation
Platzieren sie im MPG123 Download URL den Downloadlink zur MPG123 Version, die sie installieren wollen

Aktuelle URL's können unter: https://sourceforge.net/projects/mpg123/files/mpg123/ gefunden werden

Nac der platzierung des Downloadlinks muss das installationsscript ausgeführt werden, dies kann 5-10 Minuten dauern. Bitte überprüfen sie den **LOG** auf **DEBUG** Level auf den Fortschritt der Installation.

![1](/uploads/moh-livestream-helper/1.jpg "1")

# Einblick ins Script
`mv /etc/yum.repos.d/starface.repo /etc/yum.repos.d/starface.repo.copy //Starface Repository Sichern`
`cp /var/starface/module/modules/repo/75ad75a3-a423-4c45-b442-9930d2cd7702/res/0efc550c-6bd8-405a-b606-b2a2f070734a.repo /etc/yum.repos.d/starface.repo //Neues Repository platzieren`
`yum clean all //Yum Cleanup, damit die Repository Daten refresht werden`
`yum -y groupinstall "Development Tools" //Development Tools herunterladen`
`cd /usr/src //Verzeichnis Wechseln`
`wget [MPG123 URL] //MPG123.tar.gz herunterladen`
`tar -xjvf  mpg123* //tar.gz entpacken`
`cd /usr/src/mpg123*/ && ./configure;cd /usr/src/mpg123*/ && make;cd /usr/src/mpg123*/ && make install //In das Verzeichnis wechseln, die MPG123 Quelle konfigurieren, kompillieren, und anschliessend installieren`
`make clean //Make bereinigen`
`cd /usr/src && rm -r -f mpg123*; //Source verzeichnis entfernen`
`rm -f /etc/yum.repos.d/starface.repo //Repository wieder löschen`
`mv /etc/yum.repos.d/starface.repo.copy /etc/yum.repos.d/starface.repo //Original Starface Repository wieder platzieren`
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch:8018/lizenzierung
