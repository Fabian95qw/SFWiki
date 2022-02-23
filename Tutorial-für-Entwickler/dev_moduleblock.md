---
title: Entwicklung eines Modulbausteins
description: 
published: false
date: 2022-02-23T13:42:18.806Z
tags: 
editor: markdown
dateCreated: 2022-02-23T13:40:24.642Z
---

# Entwickeln eines Modulbausteins
Hier wird demonstriert, wie ein einfacher Modulbaustein in Java geschrieben, kompiliert, und in die STARFACE Importiert wird.

## Beispielbaustein
Um einen für die Starface validen Modulbaustein zu bauen, muss man eine Klasse erstellen (hier im Beispiel mit Namen "Demo"), welche die "IBaseExecutable" implementiert und die @Function definieren. 
 

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

## Erklärung der einzelnen Teile
### Function

    @Function(visibility=Visibility.Private, rookieFunction=false, description="Default") 

Hiermit definiert man den Modulbaustein. 
Visibility: Wo der Baustein ersichtlich sein soll. Privat → Nur im aktuellen Modul, Public → für alle Module. 
Rookiefunction: Ob der Baustein normal sichtbar ist, oder nur wenn der Experten-Modus aktiviert ist. 
Description: Enthält den Text, welcher im "i" des Modulbauesteins angezeigt wird

### Inputvar/Outputvar

    @InputVar(label="DEFAULT", description="DEFAULT",type=VariableType.STRING)
    public String INPUT_DEFAULT="";
    
    @OutputVar(label="DEFAULT", description="DEFAULT",type=VariableType.OBJECT)
    public Object OUTPUT_DEFAULT=""; 

Mit den Input-/Outputvars wird definiert, was für Parameter der Baustein im Modul-Editor Annimmt/Zurückgibt. 
Nach jedem @InputVar/@OutputVar muss immer das dazugehörige Java Variable Folgen, welche mit dem Wert befüllt werden soll. 

Label: Name welcher im Modul-Editor für diese Variable angezeigt wird. 
Description: Der Beschreibungstext der entsprechenden Variable 
VariableType: Was für ein Variablentyp das erwartet wird. Z.b. STRING/BOOLEAN/STARFACE_USER/STARFACE_GROUP/FILE usw.. 

Das Modul wird jeweils versuchen den VariableType zur Java-Variable zu Casten. Wenn man z.b. den VariabelType als "STRING" hinterlegt hat, die Java-Variable aber ein Integer ist, wird das Modul versuchen den Wert zu casten, und falls das Ergebnis dabei ungütlgi wird, würde es ein "null" erzeugen, ausser im Falle von BOOLEAN, dort erzeugt ein Falscher Cast immer ein "false"

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

