---
title: XML-RPC Aufrufe an Module ausführen
description: 
published: true
date: 2022-11-28T14:08:32.618Z
tags: 
editor: markdown
dateCreated: 2022-03-03T10:43:29.587Z
---

# XML-RPC Aufrufe an Module ausführen

Es besteht die möglichkeit bei Modulen RPC-Einstiegspunkte zu definieren, welche von extern abgefragt werden können.

> Jeder Person, welche korrekte Logindaten für die STARFACE Besitzt, kann XML-RPC Einstiegspunkte nutzen.
> Wir Empfehlen deshalb die Einstiegspunkte mit einem Zusätzlichem Passwort im Modul, zu schützen, so dass selbst mit gültigen STARFACE Zugangsdaten die Endpunkte nicht missbraucht werden können.
{.is-danger}

## Token berechnen
Zur Authentifizierung des Benutzers wird nicht ein Benutzernamen und Passwort benötigt, sondern man muss bereit sein Token draus berechnen.

Zur Berechnung des Tokens wird die LoginID, und das Passwort des Benutzers benötigt.
Das Token wird folgendermassen erzeugt:

Login:sha512(Login*sha512(Passwort))
Der Asterisk (\*) wird als Charakterzeichen verwendet, **es muss nichts multiplziert werden.**

Beispiel:
Login: 123
Passwort: Pass123

| Komponente | Hash/Resultat |
|------------|------|
| sha512("Pass123") | d01feaafb5359e1fa2c020a76ebb526fc75786b0b837e0c9a4dcabd58ad734efa469513cf66a272d5ef4b1b9646b4b39f50807afc8f8663e1c6bb23552b04cd6 |
| sha512("123*"+sha512("Pass123")) | 81d8af78c98b153485f7d48e3437eb735ba37f0f013c5e06ba74536776c5945694e7cde71e2effbed7b5a1d1a4566fadcd847ef4098c234052fdfd288e8b6ced|
| 123:sha512("123*"+sha512("Pass123)) | 123:81d8af78c98b153485f7d48e3437eb735ba37f0f013c5e06ba74536776c5945694e7cde71e2effbed7b5a1d1a4566fadcd847ef4098c234052fdfd288e8b6ced |

### Beispielcode

<details>
  <summary>Code (Klicken zum Anzeigen)</summary>
  
    import java.math.BigInteger;
    import java.security.MessageDigest;
    import java.security.NoSuchAlgorithmException;

    public class EntryPoint {

      public static void main(String[] args) {
        String Login = "123";
        String Password = "Pass123";
        String PW512 = sha512(Password);
        System.out.println(PW512);
        String Output512 = sha512(Login+"*"+PW512);
        System.out.println(Output512);
        String Token = Login+":"+Output512;
        System.out.println(Token);
      }

        private static String sha512(String input) 
        { 
            try { 
                // getInstance() method is called with algorithm SHA-512 
                MessageDigest md = MessageDigest.getInstance("SHA-512"); 
                // digest() method is called 
                // to calculate message digest of the input string 
                // returned as array of byte 
                byte[] messageDigest = md.digest(input.getBytes()); 
                // Convert byte array into signum representation 
                BigInteger no = new BigInteger(1, messageDigest); 
                // Convert message digest into hex value 
                String hashtext = no.toString(16); 
                // Add preceding 0s to make it 32 bit 
                while (hashtext.length() < 32) { 
                    hashtext = "0" + hashtext; 
                } 
                // return the HashText 
                return hashtext; 
            } 
            // For specifying wrong message digest algorithms 
            catch (NoSuchAlgorithmException e) { 
                throw new RuntimeException(e); 
            } 
        } 
    }
  
</details>

## Active-Directory Token berechnen
  Für das Active-Directory muss das Token anderst berechnet werden.
  Der genaue weg ist mir noch nicht bekannt.

## XML-RPC Einstiegspunkte im Modul definieren
  
### Eine Funktion erstellen

  Vorab muss man eine Funktion erstellen, welche vom XML-RPC Einstiegspunkt genutzt werden soll.
  Die Hierbei definierten Inputvars, und Outputwars werden dann wie XML-RPC befüllt bzw. abgeholt.
  
  In diesem Beispiel machen wir eine einfache Funktion, welche zwei Werte Addiert, und das Ergebnis ausgibt.
  
  ![dev_module_xml_rpc_function.png](/uploads/dev_tutorial/dev_module_xml_rpc_function.png)
  
  ![dev_module_xml_rpc_function_code.png](/uploads/dev_tutorial/dev_module_xml_rpc_function_code.png)
  
### Funktion via XML-RPC Freigeben
  Im Vordersten Tab kann man diese Funktion nun via "Rpc Entrypoints" freigeben. 
  Die XML-RPC funktion erhält einen separaten Namen zum effektiven Namen der Funktion.
  
  ![dev_module_xml_rpc_expose_function.png](/uploads/dev_tutorial/dev_module_xml_rpc_expose_function.png)
  
  
 ## XML-RPC Einstiegspunkte Ansprechen/Testen
  
  Der XML-RPC Einstiegspunkt ist nun fertig, und kann getestet werden. 
  Wir Empfehlen für einfache Tests das Programm [Postman](https://www.postman.com/)
  
### XML-RPC Einstiegspunkt Name
  Der XML-RPC Einstiegspunkt wird einmal pro instanz generiert
	Bedeutet, dass der Instanzname teil des XML-RPC aufrufs ist.
  Dies muss man entsprechend Berücksichtigen.
  
  Den Namen des XML-RPC Einstiegspunktes findet man in der Instanz im Tab "XML-RPC" (wird erst sichtbar, sobald man einen Einstiegspunkt definiert hat.
  
![dev_module_xml_rpc_function_name.png](/uploads/dev_tutorial/dev_module_xml_rpc_function_name.png)
  
 ### Aufbau des URLs
  
  Der Zugriffsurl für die XML-RPC ist: http|https://\[IP/DNS-der-STARFACE]//xml-rpc?de.vertico.starface.auth=\[Token]
  
  Beispiel: http://**192.168.200.240**/xml-rpc?de.vertico.starface.auth=**123:81d8af78c98b153485f7d48e3437eb735ba37f0f013c5e06ba74536776c5945694e7cde71e2effbed7b5a1d1a4566fadcd847ef4098c234052fdfd288e8b6ced**
  
 ### Aufbau eines XML-RPC Requests
  <details>
  <summary>XML (Klicken zum Anzeigen)</summary>

    <?xml  version="1.0"?>
    <methodCall>
	    <methodName>[XML-RPC-Einstiegspunkt]</methodName>
	    <params>
		    <param>
			    <value>
				    <struct>
						    <member>
							    <name>Variablenname1</name>
							    <value>
									    <string>Wert1</string>
						    </value>
					    </member>
					    <member>
						    <name>Variablenname2</name>
						    <value>
							    <string>Wert2</string>
						    </value>
				    </member>
			    </struct>
		    </value>
	    </param>
    </params>
    </methodCall>

  </details>

#### Beispiel für die Addition:

<details>
  <summary>XML (Klicken zum Anzeigen)</summary>

    <?xml  version="1.0"?>
    <methodCall>
	    <methodName>Example Instancename.Simplemath</methodName>
	    <params>
		    <param>
			    <value>
				    <struct>
						    <member>
							    <name>Num1</name>
							 <value>
								<string>123</string>
						    </value>
					    </member>
					    <member>
						    <name>Num2</name>
						    <value>
							    <string>321</string>
						    </value>
				    </member>
			    </struct>
		    </value>
	    </param>
    </params>
    </methodCall>

</details>



#### Beispiel Antwort

<details>
  <summary>XML (Klicken zum Anzeigen)</summary>
  
    <?xml  version="1.0"?>
    <methodResponse>
    <params>
	    <param>
		    <value>
			    <struct>
				    <member>
				    <name>Sum</name>
					    <value>
						    <double>444.0</double>
					    </value>
				    </member>
			    </struct>
		    </value>
	    </param>
    </params>
    </methodResponse>
    
</details>

  
### Postman Beispieldatei

  Diese kann im Postman Importiert werden, und enthält das Beispiel XML-RPC.
  [XML-RPC-Example.postman_collection.json](/uploads/dev_tutorial/XML-RPC-Example.postman_collection.json)
  
  
  ## XML-RPC Einstiegspunkt ohne Authentifizierung
  
 Es gibt die möglichkeit XML-RPC Einstiegspunkte ohne Tokenauthentifizierung zu erstellen.
 Hierfür muss man im Modul die Einstiegspunkte wie gewohnt definieren, und danach das Modul als .sfm Herunterladen.
 
 Die .sfm Datei muss nachher mit einem Entzipper (z.b. 7-Zip, WinRar usw..) entpackt werden.
 In der .sfm Datei befindet sich ein **module-descriptor.xml** dieser muss mit einem Editor geöffnet werden.
 
Hier sollte nun nach dem Namen des XML-RPC Einstiegspunktes gesucht werden.
Beim Type muss der Typ auf XMLRPC_noauth gewechselt werden.

Z.b für den XML-RPC Einstiegspunkt "getservicestate"

\<rpcEntryPoint id="6a76daa5-a10d-4566-9de1-e4b1bf37249d" name="**getservicestate**">
\<functionReference targetDomainId="95ac8f4b-715e-4384-84fe-0cc8ff40582f" targetId="e74e5cf9-e4b7-4102-b6c3-c329fb57e4c4" targetName="NewFunction2" targetVersion="0"/>
\<type>**XMLRPC_noauth**\</type>
\</rpcEntryPoint>

Nachdem man die .xml Editiert hat, muss man die modifizierte Datei zurück ins .sfm Packen, und dieses in der Modul-Library über das vorhandene Modul importieren.

> Bitte stellt sicher dass kein Modul-Editor Fenster von diesem Modul geöffnet ist, bevor ihr das Modul erneut importiert. Ansonsten könnte die Änderungen im xml Verloren gehen, und der Vorgang muss wiederholt werden.
{.is-warning}


Danach kann das Modul ohne Authentifizierung via: http://\[IP-der-STARFACE\]/xml-rpc angesprochen werden.

> Es ist zu Empfehlen, hier eine manuelle Authentifizierungslogik zu verbauen, um missbrauch zu verhindern. Dies kann z.b. durch einen eigens Statisch/Dynamischem Token gelöst werden, welcher bei jedem Request mitgesendet wird.
{.is-warning}



