<!-- TITLE: Office365 App mit Gerätelogin erstellen -->
# Beschreibung
Zur Nutzung einiger Office365 Spezifischen Module wird ein "App Zugang" benötigt, welcher dem Modul erlaubt, Aufträge im Office365 zu erledigen. (Z.b. Exchange Zugriff)
Hier wird kurz beschrieben, wie man so eine Office365 App erstellt.
# Erstellung einer App
Als erstes muss man sich auf https://portal.azure.com mit einem **Globalem Admin** der Organisation einloggen.
Danach wechselt man in das Azure-Active-Directory ==> App-Registrations, und erstellt dort eine neue App.
(**Dies funktioniert auch ohne entsprechende Azure AD Lizenzen**)

![Create App](/uploads/office-365-client-app/create-app.png "Create App")

## App-ID + Tentant ID Sichern

Sobald die App erstellt wurde, speichert als erstes die Application (client) ID, sowie die Directory (tenant) ID.
Diese werden später im Modul benötigt.

![App Info](/uploads/office-365-client-app/app-info.png "App Info")

## App-Berechtigungen vergeben

Damit das Modul das machen kann, was es soll, muss man dem eben erstellten App-Zugang noch Berechtigungen zuweisen. Diese können im Tab "API permissions" gesetzt werden.
Die benötigten Berechtigungen Variieren von Modul zu Modul. 
Gewisse Berechtigungen müssen durch einen Globalen Admin genehmigt werden.

![Admin Consent](/uploads/office-365-client-app/admin-consent.png "Admin Consent")
