---
title: Einrichtung der Entwicklungsumgebung (Eclipse)
description: 
published: false
date: 2022-02-23T13:41:03.288Z
tags: 
editor: markdown
dateCreated: 2022-02-18T09:55:31.658Z
---

# Einrichtung der Eclipse IDE
Ein kurzes Tutorial, wie man im Eclipse ein Projekt eröffnet, mit welchem sich STARFACE Modulbausteine erzeugen lassen.

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

##  Einrichtung der Entwicklungsumgebung in Eclipse

Man eröffnet ein ganz normales Java Project mit der Java-Version der Anlage 
**v6.x → Java 1.7
v7.x → Java 1.8**
> Achtung! Wenn die falsche Java Version gewählt wird können die Bausteine auf der Anlage nicht geladen werden. 
{.is-danger}


Danach geht man auf das Projekt → Rechtsklick → Properties → Java Build Path ==> Libraries, und fügt via "Add External Jar’s" alle JAR Dateien aus dem heruntergeladenen "lib" Verzeichnis zum Projekt hinzu. 
Danach fügen wir noch die Klassen via "Add external Class Folder" das heruntergeladene "Classes" Verzeichnis hinzu.

![eclipse_setup.png](/uploads/dev_tutorial/eclipse_setup.png)


