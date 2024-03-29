---
title: Chatstatus für einen Benutzer setzen.
description: 
published: true
date: 2023-10-09T11:15:31.410Z
tags: 
editor: markdown
dateCreated: 2022-02-23T14:08:47.870Z
---

# Beispielcode: Chatstatus für einen Benutzer lesen/setzen

In diesem Beispiel wird gezeigt, wie man den Chatstatus für einen Benutzer setzt.

## Modulbaustein Lesen der Chatpräsenz
[GetUserPresence.java](https://github.com/Fabian95qw/SFWiki/blob/master/uploads/dev_tutorial/sourcecode/chatpresence/GetUserPresence.java)

## Alte Codebeispiele
<details>
  <summary> Code 7.3 (Klicken zum Anzeigen)</summary>
  
    package si.module.examples.chatpresence;

		import org.apache.logging.log4j.Logger;
    import de.starface.bo.BusinessObjects;
    import de.starface.core.component.StarfaceComponentProvider;
    import de.starface.integration.uci.java.v30.types.UserState;
    import de.vertico.starface.module.core.model.VariableType;
    import de.vertico.starface.module.core.model.Visibility;
    import de.vertico.starface.module.core.runtime.IBaseExecutable;
    import de.vertico.starface.module.core.runtime.IRuntimeEnvironment;
    import de.vertico.starface.module.core.runtime.annotations.Function;
    import de.vertico.starface.module.core.runtime.annotations.InputVar;
    import de.vertico.starface.module.core.runtime.annotations.OutputVar;

    @Function(visibility=Visibility.Private, rookieFunction=false, description="Get the User's Chatpresence")
    public class GetUserPresence implements IBaseExecutable
    {
    //##########################################################################################

      @InputVar(label="AccountID", description="The STARFACE_USER to do this action for",type=VariableType.STARFACE_USER)
      public int AccountID=0;

      @OutputVar(label="ChatPresence", description="The currently set chatpresence",type=VariableType.STRING)
      public String ChatPresence="";

      @OutputVar(label="ChatPresenceMessage", description="The currently set presencemessage possibleValues={AVAILABLE, AWAY, DO_NOT_DISTURB ,EXTENDED_AWAY, FREE_FOR_CHAT, UNAVAILABLE}",type=VariableType.STRING)
      public String ChatPresenceMessage="";

      @OutputVar(label="Success", description="If setting the status was sucessful",type=VariableType.BOOLEAN)
      public boolean Success=false;

        StarfaceComponentProvider componentProvider = StarfaceComponentProvider.getInstance();
        //##########################################################################################


      //###################      Code Execution      ############################
      @Override
      public void execute(IRuntimeEnvironment context) throws Exception
      {
    		Logger log  = context.getLog();
        //Fetch the Required Components
        BusinessObjects BO = (BusinessObjects)context.provider().fetch(BusinessObjects.class);

        UserState userState = BO.getUserStateBO().getUserState(AccountID); //Fetch the current UserState for the accountid
        if(userState == null) //If AccountID is invalid/user does not exist
        {
          log.error("User with AccountID: "+ AccountID+ " does not exist!");
          Success = false;
          return;
        }

        ChatPresence = userState.getChatPresence().toString(); //Read out ChatPresence to String
        ChatPresenceMessage = userState.getChatPresenceMessage(); //Red out ChatMessage

      }//END OF EXECUTION
    }
  
</details>

<details>
  <summary>Code 7.2 (Klicken zum Anzeigen)</summary>
  
    package si.module.examples.chatpresence;

    import org.apache.commons.logging.Log;
    import de.starface.bo.BusinessObjects;
    import de.starface.core.component.StarfaceComponentProvider;
    import de.starface.integration.uci.java.v30.types.UserState;
    import de.vertico.starface.module.core.model.VariableType;
    import de.vertico.starface.module.core.model.Visibility;
    import de.vertico.starface.module.core.runtime.IBaseExecutable;
    import de.vertico.starface.module.core.runtime.IRuntimeEnvironment;
    import de.vertico.starface.module.core.runtime.annotations.Function;
    import de.vertico.starface.module.core.runtime.annotations.InputVar;
    import de.vertico.starface.module.core.runtime.annotations.OutputVar;

    @Function(visibility=Visibility.Private, rookieFunction=false, description="Get the User's Chatpresence")
    public class GetUserPresence implements IBaseExecutable
    {
    //##########################################################################################

      @InputVar(label="AccountID", description="The STARFACE_USER to do this action for",type=VariableType.STARFACE_USER)
      public int AccountID=0;

      @OutputVar(label="ChatPresence", description="The currently set chatpresence",type=VariableType.STRING)
      public String ChatPresence="";

      @OutputVar(label="ChatPresenceMessage", description="The currently set presencemessage possibleValues={AVAILABLE, AWAY, DO_NOT_DISTURB ,EXTENDED_AWAY, FREE_FOR_CHAT, UNAVAILABLE}",type=VariableType.STRING)
      public String ChatPresenceMessage="";

      @OutputVar(label="Success", description="If setting the status was sucessful",type=VariableType.BOOLEAN)
      public boolean Success=false;

        StarfaceComponentProvider componentProvider = StarfaceComponentProvider.getInstance();
        //##########################################################################################


      //###################      Code Execution      ############################
      @Override
      public void execute(IRuntimeEnvironment context) throws Exception
      {
        Log log  = context.getLog();
        //Fetch the Required Components
        BusinessObjects BO = (BusinessObjects)context.provider().fetch(BusinessObjects.class);

        UserState userState = BO.getUserStateBO().getUserState(AccountID); //Fetch the current UserState for the accountid
        if(userState == null) //If AccountID is invalid/user does not exist
        {
          log.error("User with AccountID: "+ AccountID+ " does not exist!");
          Success = false;
          return;
        }

        ChatPresence = userState.getChatPresence().toString(); //Read out ChatPresence to String
        ChatPresenceMessage = userState.getChatPresenceMessage(); //Red out ChatMessage

      }//END OF EXECUTION
    }
  
</details>

## Modulbaustein setzen der Chatpräsenz

[ChangeUserPresence.java](https://github.com/Fabian95qw/SFWiki/blob/master/uploads/dev_tutorial/sourcecode/chatpresence/ChangeUserPresence.java)

## Alte Codebeispiele
<details>
  <summary>Code 7.3 (Klicken zum Anzeigen)</summary>
  
    package si.module.examples.chatpresence;

		import org.apache.logging.log4j.Logger;
    import de.starface.bo.BusinessObjects;
    import de.starface.bo.events.NewUserStateEvent;
    import de.starface.core.component.StarfaceComponentProvider;
    import de.starface.core.component.events.StarfaceEventService;
    import de.starface.integration.uci.java.v30.types.UserState;
    import de.starface.integration.uci.java.v30.values.ChatPresence;
    import de.vertico.starface.module.core.model.VariableType;
    import de.vertico.starface.module.core.model.Visibility;
    import de.vertico.starface.module.core.runtime.IBaseExecutable;
    import de.vertico.starface.module.core.runtime.IRuntimeEnvironment;
    import de.vertico.starface.module.core.runtime.annotations.Function;
    import de.vertico.starface.module.core.runtime.annotations.InputVar;
    import de.vertico.starface.module.core.runtime.annotations.OutputVar;

    @Function(visibility=Visibility.Private, rookieFunction=false, description="Changes the User's Chatstate")
    public class ChangeUserPresence implements IBaseExecutable
    {
    //##########################################################################################

      @InputVar(label="AccountID", description="The STARFACE_USER to do this action for",type=VariableType.STARFACE_USER)
      public int AccountID=0;

      @InputVar(label="Chatpresence", description="The new chatstate to set",type=VariableType.STRING, possibleValues={"AVAILABLE", "AWAY", "DO_NOT_DISTURB" ,"EXTENDED_AWAY", "FREE_FOR_CHAT", "UNAVAILABLE"}) //Creates a dropdown of predefined options
      public String Chatpresence="";

      @InputVar(label="Change presencetext", description="If the presencetext has to be changed as well",type=VariableType.BOOLEAN)
      public boolean ChangeText = false;

      @InputVar(label="ChatPresenceText", description="The new text to place",type=VariableType.STRING)
      public String ChatPresenceText="";

      @OutputVar(label="Success", description="If setting the status was sucessful",type=VariableType.BOOLEAN)
      public boolean Success=false;

        StarfaceComponentProvider componentProvider = StarfaceComponentProvider.getInstance();
        //##########################################################################################


      //###################      Code Execution      ############################
      @Override
      public void execute(IRuntimeEnvironment context) throws Exception
      {
   			 Logger log  = context.getLog();
        //Fetch the Required Components
        BusinessObjects BO = (BusinessObjects)context.provider().fetch(BusinessObjects.class);
        StarfaceEventService ES = (StarfaceEventService)context.provider().fetch(StarfaceEventService.class);

        UserState userState = BO.getUserStateBO().getUserState(AccountID); //Fetch the current UserState for the accountid
        if(userState == null) //If AccountID is invalid/user does not exist
        {
          log.error("User with AccountID: "+ AccountID+ " does not exist!");
          Success = false;
          return;
        }
        userState.setChatPresence(ChatPresence.valueOf(Chatpresence)); //Set the Chatpresence of the user to the new presence selected from the dropdown
        if(ChangeText)
        {
          userState.setChatPresenceMessage(ChatPresenceText); //Set the new Chatstatustext
        }
        NewUserStateEvent Update = new NewUserStateEvent(AccountID, userState); //Create a NewUserState Event, so it can be published across all starface components
        ES.publish(Update, context.getLog()); //Fire the new Event

      }//END OF EXECUTION
    }
  
</details>

<details>
  <summary>Code 7.2 (Klicken zum Anzeigen)</summary>
  
    package si.module.examples.chatpresence;

    import org.apache.commons.logging.Log;
    import de.starface.bo.BusinessObjects;
    import de.starface.bo.events.NewUserStateEvent;
    import de.starface.core.component.StarfaceComponentProvider;
    import de.starface.core.component.events.StarfaceEventService;
    import de.starface.integration.uci.java.v30.types.UserState;
    import de.starface.integration.uci.java.v30.values.ChatPresence;
    import de.vertico.starface.module.core.model.VariableType;
    import de.vertico.starface.module.core.model.Visibility;
    import de.vertico.starface.module.core.runtime.IBaseExecutable;
    import de.vertico.starface.module.core.runtime.IRuntimeEnvironment;
    import de.vertico.starface.module.core.runtime.annotations.Function;
    import de.vertico.starface.module.core.runtime.annotations.InputVar;
    import de.vertico.starface.module.core.runtime.annotations.OutputVar;

    @Function(visibility=Visibility.Private, rookieFunction=false, description="Changes the User's Chatstate")
    public class ChangeUserPresence implements IBaseExecutable
    {
    //##########################################################################################

      @InputVar(label="AccountID", description="The STARFACE_USER to do this action for",type=VariableType.STARFACE_USER)
      public int AccountID=0;

      @InputVar(label="Chatpresence", description="The new chatstate to set",type=VariableType.STRING, possibleValues={"AVAILABLE", "AWAY", "DO_NOT_DISTURB" ,"EXTENDED_AWAY", "FREE_FOR_CHAT", "UNAVAILABLE"}) //Creates a dropdown of predefined options
      public String Chatpresence="";

      @InputVar(label="Change presencetext", description="If the presencetext has to be changed as well",type=VariableType.BOOLEAN)
      public boolean ChangeText = false;

      @InputVar(label="ChatPresenceText", description="The new text to place",type=VariableType.STRING)
      public String ChatPresenceText="";

      @OutputVar(label="Success", description="If setting the status was sucessful",type=VariableType.BOOLEAN)
      public boolean Success=false;

        StarfaceComponentProvider componentProvider = StarfaceComponentProvider.getInstance();
        //##########################################################################################


      //###################      Code Execution      ############################
      @Override
      public void execute(IRuntimeEnvironment context) throws Exception
      {
        Log log  = context.getLog();
        //Fetch the Required Components
        BusinessObjects BO = (BusinessObjects)context.provider().fetch(BusinessObjects.class);
        StarfaceEventService ES = (StarfaceEventService)context.provider().fetch(StarfaceEventService.class);

        UserState userState = BO.getUserStateBO().getUserState(AccountID); //Fetch the current UserState for the accountid
        if(userState == null) //If AccountID is invalid/user does not exist
        {
          log.error("User with AccountID: "+ AccountID+ " does not exist!");
          Success = false;
          return;
        }
        userState.setChatPresence(ChatPresence.valueOf(Chatpresence)); //Set the Chatpresence of the user to the new presence selected from the dropdown
        if(ChangeText)
        {
          userState.setChatPresenceMessage(ChatPresenceText); //Set the new Chatstatustext
        }
        NewUserStateEvent Update = new NewUserStateEvent(AccountID, userState); //Create a NewUserState Event, so it can be published across all starface components
        ES.publish(Update, context.getLog()); //Fire the new Event

      }//END OF EXECUTION
    }
  
</details>