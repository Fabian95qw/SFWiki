---
title: Einrichtung der Entwicklungsumgebung (IntelliJ)
description: 
published: true
date: 2022-02-23T13:38:44.905Z
tags: 
editor: markdown
dateCreated: 2022-02-23T13:38:44.905Z
---

# Einrichtung der IntelliJ IDEA
Ein kurzes Tutorial, wie man im IntelliJ IDEA ein Projekt eröffnet, mit welchem sich STARFACE Modulbausteine erzeugen lassen.

##  Download der benötigten Bibliotheken + Klassen

Sämtliche Klassen, welche für die Programmierung von Starface Bausteinen benötigt werden, liegen auf jeder Starface Anlage. Die Daten können z.b. via WinSCP (SSH) abgeholt werden.

Benötigt werden das Bibliotheksverzeichnis und das Klassenverzeichnis. Das Bibliotheksverzeichnis enthält sämtliche Bibliotheken, die auf der Starface zur Verfügung stehen, das Klassenverzeichnis sämtliche Starface Klassen.

Die Verzeichnisse sind zu finden unter
**vor v7.x**
/var/lib/tomcat6/webapps/localhost/starface/WEB-INF/lib
/var/lib/tomcat6/webapps/localhost/starface/WEB-INF/classes
**ab v7.x**
/opt/tomcat/webapps/localhost/starface/WEB-INF/lib
/opt/tomcat/webapps/localhost/starface/WEB-INF/classes

Diese Daten müssen nicht im Projektverzeichnis abgelegt werden.

## Einrichten der Entwicklungsumgebung IntelliJ IDEA

Man startet ein neues Projekt vom Typ "Java" und wählt als Project SDK die zur Starface Anlage passende Java-Version.

**v6.x → Java 1.7
v7.x → Java 1.8**

> Achtung! Wenn die falsche Java Version gewählt wird können die Bausteine auf der Anlage nicht geladen werden. 
> 
{.is-danger}

Anschließend öffnet man über "File" die "Project Structure" und fügt unter "Libraries" die heruntergeladenen Pfade hinzu, einmal das "lib" Verzeichnis und einmal das "classes" Verzeichnis.

Unter "Modules" wählt man das akutelle Module aus und stellt den "Scope" der beiden Libraries von "compile" auf "provided" (da die Libs und Klassen auf der Starface zur Verfügung stehen und nicht mit kompiliert werden müssen).

Falls allerdings auch lokal getestet werden soll, z.B. einzelne Methoden in Testklassen, kann diese Einstellung dazu führen, dass es zu "java.lang.NoClassDefFoundError" Fehlermeldungen kommt. In dem Falle sollte man die Einstellung wieder auf "compile" stellen.
