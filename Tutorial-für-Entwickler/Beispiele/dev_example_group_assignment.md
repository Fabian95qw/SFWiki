---
title: Gruppenmitgliedschaft eines Benutzer de-aktivieren
description: 
published: true
date: 2022-10-14T08:28:22.678Z
tags: 
editor: markdown
dateCreated: 2022-03-07T15:43:34.354Z
---

# Gruppenmitgliedschaft eines Benutzer de-aktivieren

Beispiel wie die Mitgliedschaft eines Benutzers de-aktiviert wird. 


## Beispielcode

<details>
  <summary> Code 7.3 (Klicken zum Anzeigen)</summary>
  
    import java.util.List;
    import de.starface.core.component.StarfaceComponentProvider;
    import de.vertico.starface.module.core.model.VariableType;
    import de.vertico.starface.module.core.model.Visibility;
    import de.vertico.starface.module.core.runtime.IBaseExecutable;
    import de.vertico.starface.module.core.runtime.IRuntimeEnvironment;
    import de.vertico.starface.module.core.runtime.annotations.Function;
    import de.vertico.starface.module.core.runtime.annotations.InputVar;
    import de.vertico.starface.persistence.connector.GroupHandler;
    import de.vertico.starface.persistence.databean.core.Group;
    import de.vertico.starface.persistence.databean.core.GroupUserSetting;

    @Function(visibility=Visibility.Private, rookieFunction=false, description="")
    public class ChangeUserAssignmentforGroup implements IBaseExecutable 
    {
      //##########################################################################################

      @InputVar(label="STARFACE_USER", description="",type=VariableType.STARFACE_USER)
      public Integer STARFACE_USER=-1;

      @InputVar(label="STARFACE_GROUP", description="",type=VariableType.STARFACE_GROUP)
      public Integer STARFACE_GROUP=-1;

      @InputVar(label="Assigned", description="TRUE == ASSIGN TO GROUP | FALSE == UNASSIGN FROM GROUP",type=VariableType.BOOLEAN)
      public boolean Assigned=false;

        StarfaceComponentProvider componentProvider = StarfaceComponentProvider.getInstance(); 
        //##########################################################################################

      //###################			Code Execution			############################	
      @Override
      public void execute(IRuntimeEnvironment context) throws Exception 
      {
        GroupHandler GH = (GroupHandler)context.provider().fetch(GroupHandler.class); //Fetch Group Handler

        Group EG = GH.getGroupForAccount(STARFACE_GROUP);  //Fetch Group based on Input Variable

        List<GroupUserSetting> Settings = GH.getGroupUserSettingListForGroupId(EG.getId()); //Fetch the Group User Assignment Settings. This is reflective of the DB. There is one GroupUserAssignment per User per Group.

        for(GroupUserSetting Setting : Settings) //Foreach Setting
        {
          if(Setting.getUserData().getAccountId() == STARFACE_USER) //If the Setting Matches the User we're looking for
          {
            Setting.setAvailable(Assigned); //Set his availability. True ==> Ticked, False == Unticked
            GH.saveGroupUserSetting(Setting); //Save the Change to the Settings.
            break;
          }
        }
      }//END OF EXECUTION
    }
  
  </details>

<details>
  <summary> Code 7.2 (Klicken zum Anzeigen)</summary>
  
    import java.util.List;
    import de.starface.core.component.StarfaceComponentProvider;
    import de.vertico.starface.module.core.model.VariableType;
    import de.vertico.starface.module.core.model.Visibility;
    import de.vertico.starface.module.core.runtime.IBaseExecutable;
    import de.vertico.starface.module.core.runtime.IRuntimeEnvironment;
    import de.vertico.starface.module.core.runtime.annotations.Function;
    import de.vertico.starface.module.core.runtime.annotations.InputVar;
    import de.vertico.starface.persistence.connector.GroupHandler;
    import de.vertico.starface.persistence.databean.core.Group;
    import de.vertico.starface.persistence.databean.core.GroupUserSetting;

    @Function(visibility=Visibility.Private, rookieFunction=false, description="")
    public class ChangeUserAssignmentforGroup implements IBaseExecutable 
    {
      //##########################################################################################

      @InputVar(label="STARFACE_USER", description="",type=VariableType.STARFACE_USER)
      public Integer STARFACE_USER=-1;

      @InputVar(label="STARFACE_GROUP", description="",type=VariableType.STARFACE_GROUP)
      public Integer STARFACE_GROUP=-1;

      @InputVar(label="Assigned", description="TRUE == ASSIGN TO GROUP | FALSE == UNASSIGN FROM GROUP",type=VariableType.BOOLEAN)
      public boolean Assigned=false;

        StarfaceComponentProvider componentProvider = StarfaceComponentProvider.getInstance(); 
        //##########################################################################################

      //###################			Code Execution			############################	
      @Override
      public void execute(IRuntimeEnvironment context) throws Exception 
      {
        GroupHandler GH = (GroupHandler)context.provider().fetch(GroupHandler.class); //Fetch Group Handler

        Group EG = GH.getGroupForAccount(STARFACE_GROUP);  //Fetch Group based on Input Variable

        List<GroupUserSetting> Settings = GH.getGroupUserSettingListForGroupId(EG.getId()); //Fetch the Group User Assignment Settings. This is reflective of the DB. There is one GroupUserAssignment per User per Group.

        for(GroupUserSetting Setting : Settings) //Foreach Setting
        {
          if(Setting.getUserData().getAccountId() == STARFACE_USER) //If the Setting Matches the User we're looking for
          {
            Setting.setAvailable(Assigned); //Set his availability. True ==> Ticked, False == Unticked
            GH.saveGroupUserSetting(Setting); //Save the Change to the Settings.
            break;
          }
        }
      }//END OF EXECUTION
    }
  
  </details>
