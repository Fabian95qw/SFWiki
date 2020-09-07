<!-- TITLE: Office365 App mit ClientSecret erstellen -->
# Beschreibung
Zur Nutzung einiger Office365 Spezifischen Module wird ein "App Zugang" benötigt, welcher dem Modul erlaubt, Aufträge im Office365 zu erledigen. (Z.b. Exchange Zugriff)
Hier wird kurz beschrieben, wie man so eine Office365 App erstellt.
# Erstellung einer App
Als erstes muss man sich auf https://portal.azure.com mit einem **Globalem Admin** der Organisation einloggen.
Danach wechselt man in das Azure-Active-Directory ==> App-Registrations, und erstellt dort eine neue App.

![Create App](/uploads/office-365-client-app/create-app.png "Create App")

Sobald die App erstellt wurde, speichert als erstes die Application (client) ID, sowie die Directory (tenant) ID.
Diese werden später im Modul benötigt.