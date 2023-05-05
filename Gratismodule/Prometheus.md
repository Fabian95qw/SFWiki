---
title: Prometheus Zugriff freischalten
description: 
published: true
date: 2023-05-05T05:52:25.804Z
tags: 
editor: markdown
dateCreated: 2023-05-04T14:04:49.316Z
---

# Beschreibung
Dieses Modul schaltet den Zugriff auf die Prometheus Plattform auf der STARFACE frei.

# Konfiguration

![1.png](/uploads/prometheus/1.png)

## Listener Adresse
Standardmässig hört der Prometheus nur auf localhost (127.0.0.1) zu. Damit dieser von aussen erreichbar wird, muss diese auf die STARFACE IP geändert werden. 

> Der Port von Prometheus weicht vom Standardport ab, es wird der Port 9999 statt 9090 verwendet.
{.is-info}


## Zugelassene IP's
Da es keinen Passwortschutz gibt, müssen zwingend IP's fürs Whitelsiting angegeben werden.
Leere Liste == Kein Zugriff möglich.
IP's können als Einzelne IPs, oder mit CIDR angegeben werden. Z.b. 192.168.1.1, 192.168.2.0/24
> Wenn IP's entfernt werden, bleiben diese trotzdem bis zum Neustart der STARFACE freigeschaltet!
{.is-warning}

## Modul Entfernen
> Wenn das Modul Entfernt wird, wird der Prometheus automatisch wieder auf 127.0.0.1 zurückgesetzt.
{.is-warning}

## Oberfläche

![2.png](/uploads/prometheus/2.png)


# Downloads & Lizenzierung
Für Downloads besuchen sie bitte http://module.si-solutions.ch/
Für Infos über die Lizenzierung siehe: http://wiki.si-solutions.ch/de/lizenzierung