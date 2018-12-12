<!-- TITLE: Let's Encrypt -->
# Beschreibung
Modul, welches es erlaubt Let's Encrypt Zertifikate einzurichten inklusive auto-renewal
**Gratislizenz: E334T-Y2I2X-X4AZZ-RKZ9F-GVKF6**
# Konfiguration
```diff
- Um einen korrekten Ablauf zu gewährleisten muss das Modul Schritt, für Schritt ausgefüllt werden, und zwischen jedem Schritt zwingend gespeichert werden (nicht übernehmen), um einen korrekten Ablauf zu garantieren.
```
## Automatisierung & ACME-Konfiguration
Bevor das Modul überhaupt einen Antrag auf ein SSL-Zertifikat stellen kann, muss ein acme Server gewählt werden.

Die Let's Encrypt Typsichen Server sind:

* Testumgebung: acme://letsencrypt.org/staging
* Produktivumgebung: acme://letsencrypt.org

### Datensatz Löschen
Löscht alle Informationen auf der Starface, welche durch das Modul generiert wurden.

```diff
- Bitte Sicherstellen, dass die Haken bei "Akzeptiere ACME EULA" sowie "Challenge Erfüllt" entfernt wurden.
```
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch:8018/lizenzierung