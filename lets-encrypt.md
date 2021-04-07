---
title: Let's Encrypt
description: 
published: true
date: 2021-04-07T11:35:21.835Z
tags: 
editor: markdown
dateCreated: 2021-04-07T11:35:06.671Z
---

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

* Testumgebung: https://acme-staging-v02.api.letsencrypt.org/directory 
* Produktivumgebung: https://acme-v02.api.letsencrypt.org/directory

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

## 2. Authorisierung/Challenge
### Domäne Angeben
Im 2. Schritt muss zuerst eine Domäne angegeben werden, für welche die Challenge ausgeführt werden soll, sowie der Challenge Typ DNS/HTTP gewählt werden.
```diff
- Nach diesem Schritt muss das Modul zwingend gespeichert werden!
```
![Step 2](/uploads/lets-encrypt/step-2.gif "Step 2")

### Challenge erfüllen
Wenn das Modul zuvor korrekt abgespeichert wurde, sollten nun die Felder "Challenge Entry", und "Challenge-Content" gefüllt sein.
Diese Challenge muss nun zuerst erfüllt werden.

![Step 3](/uploads/lets-encrypt/step-3.gif "Step 3")
![Step 4](/uploads/lets-encrypt/step-4.jpg "Step 4")

### Challenge bestätigen
Wenn die Challenge nun korrekt auf dem DNS-Server, oder Webserver ausgeführt wurde, kann der Haken bei "Challenge Erfüllt" gesetzt werden, um das Modul fortzusetzen.
```diff
- Nach diesem Schritt muss das Modul zwingend gespeichert werden!
```
![Step 5](/uploads/lets-encrypt/step-5.gif "Step 5")

## 3. Zertifikat anfordern
Wenn die Challenge Erfüllt wurde, kann man nun sein Zertifikat anfordern. 
Zur Prüfung, ob die Challenge korrekt Erfüllt wurde, kann man den Status im Feld "Challenge Status" prüfen.
```diff
- Nach diesem Schritt muss das Modul zwingend gespeichert werden!
```
![Step 6](/uploads/lets-encrypt/step-6.gif "Step 6")

## 4. Zertifikatserstellungseintrag überprüfen.
Wenn bis jetzt alles korrekt abgelaufen ist, müsste man nun im Modul prüfen können, ob das Zertifikat ausgestellt wurde.

![Step 7](/uploads/lets-encrypt/step-7.gif "Step 7")

```diff
- Damit das Zertifikat vom Webserver verwendet wird, muss die Starface neu gestartet werden.
```
## E-Mail Paket
Ermöglicht das Senden aller Daten des ACME-Vorgangs per E-Mail.

Enthalten sind:
* Account Registrierungs Private Key File (SessionPK.pem)
*  Certificate Private Key File (CertPK.pem) (Exportiert aus dem Tomcat KeyStore, gleicher PK, welcher von der Starface für die Webseitenzertifikate verwendet wird)
*  RegistrationURI (RegistrationURI.txt). (Dieser URI enthält die Registrierungslocation. Wird u.a. für die Löschung/Deaktivierung des Accounts benötigt.)
*  Letzten CSR (CertCSR.csr)
*  Letztes erstelltest Zertifikat (Certificate.cer)
*  Zertifikatskette für letztes Zertifikat (CACertificate.cer) (RootCA, Intermediate usw..)
# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.nucom.ch/
Für Infos über die Lizenzierung siehe: http://wiki.nucom.ch/lizenzierung