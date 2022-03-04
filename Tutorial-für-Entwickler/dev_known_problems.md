---
title: Stolpersteine
description: 
published: false
date: 2022-03-04T09:01:46.268Z
tags: 
editor: markdown
dateCreated: 2022-03-04T08:44:24.045Z
---

# Stolpersteine

Ich erkläre hier kurz einige mir bekannten Stolpersteine mit den Modulkomponenten.

## Verlust der Kontroller über Threads
Wenn man ein Modul im Modul Designer editiert/speichert, oder das Modul Updatet, wird eine neue revision des Moduls erzeugt. 

Falls das Modul zu diesem Zeitpunkt ein aktives Thread hat, wird dieses zusammen mit den alten Modulkomponenten weiter ausgeführt.  Alle Modulklassen werden komplett neu instanziert inkl. aller statischen Objekte

Wenn ihr also eigene Dienste, Runnables ect. im Modul erzeugt, welche nach der initialisierung des Moduls unabhängig davon Laufen, müssen diese vorher von Hand gestoppt werden.

> Sobald die kontrolle über die Thread verloren wurde, kann man das System nur noch neu starten, um diese loszuwerden, da diese teil des TomCat Prozesses sind {.is-danger}

### Beispiel Kontrollverlust
Wir haben ein Einfaches Thread, welches nur zählen soll. Dieses wird via Modulbaustein registriert, und in einer statischen Variable gespeichert, so dass bei einem erneuten Aufruf kein weiteres Thread erzeugt wird.

#### Counter.class
    import org.apache.commons.logging.Log;
    public class Counter implements Runnable 
    {
      private Log log = null;
      private Integer Count = 0;
      
      public Counter(Log log)
      {
        this.log=log;
        log.debug("Hello I'm a counter");
      }

      @Override
      public void run() 
      {
        while(true)
        {
          log.debug("Count: "+ Count);
          Count = Count++;
          try
          {
            Thread.sleep(1000);
          } 
          catch (InterruptedException e) 
          {
            break;
          }
        }		
      }

    }


#### StartCounter.class
    @Function(visibility=Visibility.Private, rookieFunction=false, description="")
    public class StartCounter implements IBaseExecutable 
    {
      private static Thread CounterThread = null; //Static Thread Storage

      @Override
      public void execute(IRuntimeEnvironment context) throws Exception 
      {
        Log log = context.getLog();

        if(CounterThread == null)
        {
          log.debug("Creating new Counter!");
          Counter C = new Counter(log);
          CounterThread = new Thread(C);
          CounterThread.start();
        }
      }
    }

#### Erzeugter Log:
- Creating new Counter!
- Hello I'm a counter
- Count: 0
- Count: 1
- Count: 2 ...

#### Nach weiterem Speichern:
Wird das Modul nun gespeichert, wenn das Thread bereits läuft, so verfallen alle Objekte, inkl. der statischen.

Das Modul wird nun im Modul Designer gespeichert, während der Counter Läuft, das folgende ist das Ergebnis:

- Creating new Counter!
- Hello I'm a counter
- Count: 0
- Count: 1
- Count: 2
- Count: 3
- \[Modul wird im Deisgner gespeichert]
**- Creating new Counter!**
- Count: 4
**- Hello I'm a counter**
**- Count: 0**
- Count: 5
**- Count: 1**
- Count: 6
**- Count: 2**
- Count: 7
**- Count: 3**
...
## Verlust der Kontrolle über Listener
Creating new Counter!