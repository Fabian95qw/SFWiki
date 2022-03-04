---
title: Stolpersteine
description: 
published: true
date: 2022-03-04T09:30:13.349Z
tags: 
editor: markdown
dateCreated: 2022-03-04T08:44:24.045Z
---

# Stolpersteine

Ich erkläre hier kurz einige mir bekannten Stolpersteine mit den Modulkomponenten.

## Verlust der Kontrolle über Threads/Listener
Wenn man ein Modul im Modul Designer editiert/speichert, oder das Modul Updatet, wird eine neue revision des Moduls erzeugt. 

Falls das Modul zu diesem Zeitpunkt ein aktives Thread hat, wird dieses zusammen mit den alten Modulkomponenten weiter ausgeführt. Alle Modulklassen werden komplett neu instanziert inkl. aller statischen Objekte

Wenn ihr also eigene Dienste, Runnables, Listener ect. im Modul erzeugt, welche nach der initialisierung des Moduls unabhängig davon Laufen, müssen diese vorher von Hand gestoppt werden.

> Sobald die kontrolle über die Thread verloren wurde, kann man das System nur noch neu starten, um diese loszuwerden, da diese teil des TomCat Prozesses sind {.is-danger}

Das Wichtigste deshalb:
> Im Modul eine möglichkeit einbauen, alle Threads, Runnabled, Listener etc. zu stoppen/de-registrieren. Z.b. wenn das Modul deaktiviert wird, oder mit einer Checkbox/Dropdown
{.is-success}

> Partner/Kunden darauf hinweisen, dass sie die Dienste im Modul stoppen müssen
{.is-success}

### Beispiel Kontrollverlust Threads
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
### Beispiel Kontrollverlust Listener
Wir haben einen Listener, welcher jedes mal, wenn sich der DND Status des Users ändert einen Log-Eintrag erzeugt.
Dieser wird via Modulbaustein registriert, und in einer statischen Variable gespeichert, damit er nicht wiederholt registriert wird.

#### ExampleListener.class
    public class ExampleListener 
    {
      private Log log = null;
      public ExampleListener(Log log)
      {
        this.log=log;
        log.debug("Hello I'm a Example Listener");
      }

        @EventSubscriber 
        public void onDoNotDistrubSettingChangedEvent(DoNotDistrubSettingChangedEvent Event)
        {
          log.debug("DND State for:" + Event.getAccountId() +" is " + Event.isDoNotDisturbSetting());
        }
    }

#### RegisterListener.class
    @Function(visibility=Visibility.Private, rookieFunction=false, description="")
    public class RegisterListener implements IBaseExecutable 
    {
      private static ExampleListener Example = null; //ExampleListener static Storage

      @Override
      public void execute(IRuntimeEnvironment context) throws Exception 
      {
        Log log = context.getLog();
        if(Example == null)
        {
          log.debug("Registering new Listener!");
          Example = new ExampleListener(log);
          StarfaceEventService SES = context.provider().fetch(StarfaceEventService.class);
          SES.subscribe(Example);
        }
      }
    }



#### Erzeugter Log
- Registering new Listener!
- Hello I'm a Example Listener
- DND State for: 1000 is true
- DND State for: 1000 is false

#### Erzeugter Log nach erneutem Speichern
Wird das Modul nun gespeichert, ohne dass der Listener de-registriert wird, verfallen alle Objekte, inkl. der statischen.

Das Modul wird nun im Modul Designer gespeichert, während der Listener registriert ist. Das folgende ist das Ergebnis:

- Registering new Listener!
- Hello I'm a Example Listener
- DND State for: 1000 is true
- DND State for: 1000 is false
- \[Modul wird gespeichert]
**- Registering new Listener!**
**- Hello I'm a Example Listener**
- DND State for: 1000 is true
**- DND State for: 1000 is true**
- DND State for: 1000 is false
**- DND State for: 1000 is false**
