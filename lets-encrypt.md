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

## 1. Account erstellen & EULA Akzeptieren
### Account erstellen
Um den Acme-Dienst zu Nutzen, muss eine E-Mail Adresse angegeben werden. Diese wird genutzt, um z.b. über Auslaufende Zertifikate zu informieren.

### Akzeptiere EULA
Ihr müsst vorab die EULA von Let's Encrypt Akzeptieren: https://letsencrypt.org/repository/
```diff
- Nach diesem Schritt muss das Modul zwingend gespeichert werden!
```

![Step 1](/uploads/lets-encrypt/step-1.gif "Step 1")
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch:8018/lizenzierung