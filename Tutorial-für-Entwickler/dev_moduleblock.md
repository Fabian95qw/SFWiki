---
title: Entwicklung eines Modulbausteins
description: 
published: true
date: 2022-03-04T11:52:09.015Z
tags: 
editor: markdown
dateCreated: 2022-02-23T13:40:24.642Z
---

# Entwickeln eines Modulbausteins
Hier wird demonstriert, wie ein einfacher Modulbaustein in Java geschrieben, kompiliert, und in die STARFACE Importiert wird.

## Beispielbaustein
Um einen für die Starface validen Modulbaustein zu bauen, muss man eine Klasse erstellen (hier im Beispiel mit Namen "Demo"), welche die "IBaseExecutable" (Kein Call-Processing) oder "IAGIJavaExecutable"(Call-Processing mit Anruferinformationen) implementiert und die @Function definieren. 
<details>
  <summary>Code (Klicken zum Anzeigen)</summary>
  

    import de.vertico.starface.module.core.model.VariableType;
    import de.vertico.starface.module.core.model.Visibility;
    import de.vertico.starface.module.core.runtime.IBaseExecutable;
    import de.vertico.starface.module.core.runtime.IRuntimeEnvironment;
    import de.vertico.starface.module.core.runtime.annotations.Function;
    import de.vertico.starface.module.core.runtime.annotations.InputVar;
    import de.vertico.starface.module.core.runtime.annotations.OutputVar;
    import org.apache.commons.logging.Log;  
    
    @Function(visibility=Visibility.Private, rookieFunction=false, description="Default")
    public class Demo implements IBaseExecutable
    {
    	//##########################################################################################
    
    	@InputVar(label="DEFAULT", description="DEFAULT",type=VariableType.STRING)
    	public String INPUT_DEFAULT="";
    
    	@OutputVar(label="DEFAULT", description="DEFAULT",type=VariableType.OBJECT)
    	public Object OUTPUT_DEFAULT="";
    	//##########################################################################################
    
    	//################### Code Execution ############################
    	@Override
    	public void execute(IRuntimeEnvironment context) throws Exception
    	{
    		Log log = context.getLog();
    		log.debug("Hello World!"); 
    		log.debug(INPUT_DEFAULT); 
    		OUTPUT_DEFAULT = "10"; 
    	} //END OF EXECUTION
    } 

  </details>

## Erklärung der einzelnen Teile
### Function

    @Function(visibility=Visibility.Private, rookieFunction=false, description="Default") 

Hiermit definiert man den Modulbaustein. 
Visibility: Wo der Baustein ersichtlich sein soll. Privat → Nur im aktuellen Modul, Public → für alle Module. 
Rookiefunction: Ob der Baustein normal sichtbar ist, oder nur wenn der Experten-Modus aktiviert ist. 
Description: Enthält den Text, welcher im "i" des Modulbauesteins angezeigt wird
Das ganze ist equivalent, zu der Funktionsdefinition im Modul.

![dev_function.png](/uploads/dev_tutorial/dev_function.png)

### Inputvar/Outputvar

    @InputVar(label="Inputname", description="Example Input",type=VariableType.STRING)
    public String Input1="";
    
    @OutputVar(label="Outputname", description="Example Output",type=VariableType.STRING)
    public String Output1="";

Mit den Input-/Outputvars wird definiert, was für Parameter der Baustein im Modul-Editor Annimmt/Zurückgibt. 
Nach jedem @InputVar/@OutputVar muss immer die dazugehörige **public** Java Variable Folgen, welche mit dem Wert befüllt werden soll. 

Label: Name welcher im Modul-Editor für diese Variable angezeigt wird. 
Description: Der Beschreibungstext der entsprechenden Variable 
VariableType: Was für ein Variablentyp das erwartet wird. Z.b. STRING/BOOLEAN/STARFACE_USER/STARFACE_GROUP/FILE usw.. 

Das Modul wird jeweils versuchen den VariableType zur Java-Variable zu Casten. Wenn man z.b. den VariabelType als "STRING" hinterlegt hat, die Java-Variable aber ein Integer ist, wird das Modul versuchen den Wert zu casten, und falls das Ergebnis dabei ungültig wird, würde es ein "null" erzeugen, ausser im Falle von BOOLEAN, dort erzeugt ein Falscher Cast immer ein "false"

Das ganze ist equivalent zu den Input/Output Variables im Modul.

![dev_variables.png](/uploads/dev_tutorial/dev_variables.png)

### Execute/Context

    @Override
    public void execute(IRuntimeEnvironment context) throws Exception
    {
    	Log log = context.getLog(); //Hole den Log des Moduls
    	log.debug("Hello World!"); //Schreibe Hallo Welt ins Debug Log des Moduls
    	log.debug(INPUT_DEFAULT); //Schreibe den Inhalt der dem Modul Mitgegeben wurde ins Debug Log
    	OUTPUT_DEFAULT = "10"; //Setze die Output Variable auf 10.
    } //END OF EXECUTION 

Die Effektive Ausführung des Codes beginnt beim “execute” hierbei erhält man eine IRuntimeEnvironment Variable. Dies ist der 
Context der Starface. Damit kann man auf alle Komponenten zugreifen. 

#### Zugriff auf Starface Funktionen via Context 
Mit dem Context können auf alle Starface Funktionen zugegriffen werden. Wenn man etwas Spezifisches Sucht sollte man das Classes Verzeichnis danach 
durchsuchen. 
Für die Meisten Starface Funktionen gibt es ein entsprechendes "BusinessObject".
Z.b. ich will etwas mit den Telefonen machen. Ich suche nach "Phone im Classes Verzeichnis". Es gibt eine Klasse "PhoneBussinesObject".

Jede Klasse kann mit dem Befehl: 
Klassenname Variablenname = (Klassenname)context.provider().fetch(Klassenname.class); abgeholt werden. 

Z.b. das PhoneBusinessObject 
PhoneBusinessObject PBO = (PhoneBusinessObject)context.provider().fetch(PhoneBusinessObject.class);

Mehr Details, wo die verschiedenen Funktionen zu finden sind gibts in einem separaten Wiki-Artikel

#### Aufrufen von anderen Modulbausteinen
Man kann im eigenen Code andere Modulbausteine ausführen, die meisten haben eine Klasse, die genau gleich heisst, wie der dazugehörige baustein. Oder teilweise auch mit einem "2,3,4 etc.." dahinter, da es mit STARFACE Updates verschiedene Revisionen des Bausteines gab.

Die Klassen findet man im: **WEB-INF\classes\de\vertico\starface\module\core\runtime\functions**\callHandling\call

Z.b.:

<details>
  <summary>Code (Klicken zum Anzeigen)</summary>

					GetUsersOfGroup2 GUS = new GetUsersOfGroup2(); //Der Modulbaustein GetUsersofGroup
 					//InputVariablen befüllen
					GUS.groupId = 1000; 
					GUS.activeOnly = true;
					GUS.excludeDND=false;
					try
					{
						GUS.execute(context); //Den Modulbaustein ausführen
					}
					catch(Exception e) //Alle Bausteine werfen immer eine Exception e
					{
						LogHelper.EtoStringLog(log, e);
					}
					
					for(Integer STARFACE_USER : GUS.usersOfGroup)
					{
						log.debug("Member: " + STARFACE_USER);
					}

  </details>
  
![other_moduleblock_example](/uploads/dev_tutorial/other_moduleblock_example.png)


# Exportieren eines Bausteins für die Anlage
Um einen Baustein auf der Anlage zu importieren, muss man diesen zuerst als kompilierte .class Datei Exportieren. 

## Eclipse IDE

Rechtsklick auf den entsprechenden Baustein im Project Explorer → Export → JAR File → Haken bei "Export generated class files and resources" aktivieren, und speichert es ab. 
Die .JAR Datei öffnet man dann z.b. mit 7-ZIP und extrahiert die .class Datei. 

## IntelliJ IDEA
Rechtsklick auf das Projekt oder Ordner oder Klassendatei → Build Module "Modulname". Die .class Datei wird im "out" Verzeichnis des Projektes abgelegt.

## Einspielen des Bausteins
Anschließend geht man im Starface Modul Editor auf "Resources", und fügt eine neue Resource hinzu. Dort muss man nun die zuvor entpackte bzw. kompilierte .class Datei hochladen. 
Nach erfolgtem Upload auf "Apply" klicken. 
Der Baustein ist nun, sofern alles richtig gemacht wurde, unter "Compontents → Public → [Eigener Modulname] → Demo" auffindbar. 

## Laden Zusätzliche Libraries
Falls Zusätzliche Libraries, welche auf der STARFACE nicht vorhanden sind, für die Bausteine benötigt werden, so können diese Ebenfalls via "Resources" in das Modul hochgeladen werden.

> Libraries, welche bereits eine andere Version von der STARFACE seite beziehen können nicht in zwei Versionen verwendet werden!
> Die Version, welche im STARFACE Lib Ordner liegt hat immer vorrang.
{.is-danger}

