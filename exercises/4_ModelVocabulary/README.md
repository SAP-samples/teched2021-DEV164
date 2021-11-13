# Model Businenss Rules Vocabulary 

## Table of Contents

## Table of Contents
- [Author, Activate and Deploy Business Rules](#section1)
    - [Overview](#section1-overview)
    - [Create Project](#section1-createproject)
    - [Create Data Object](#section1-dataobject)
    - [Summary](#Summary)
   




## Author and  Activate  Data Objects <a name="section1"></a>
### Overview <a name="section1-overview"></a>

The exercise is based on authoring Data Object, using SAP Business Rules service. The Data Object is used in the next exercise to associate to a Process Template to generate start and step conditions.  
  
### Create Project <a name="section1-createproject"></a>

1. Open *Workflow Management Launchpad* and click to open **Manage Rule Projects**.
    - Login with trial username and passwords <p>
    
    <img src="images/launchpad.png" width="600">
  
2. Click **+** to create a new business rules project.

    <img src="images/createproject_1.png" width="600">

3. In the *New Project* screen, do the following:
    - Enter **CAPEX_00** in the **Name** box.
    - Enter **Capital Expenditure Rules** in the **Label** box.
    - Enter **Business rules to determine approvers for new investments in capital expenditure process** in **Description** box.
    - Select **2.0** as the **Expression Language**.
    - Click **Save** 
    <p>
     <img src="images/createproject_2.png" width="600">

#### Your business rules project is created with the needed configurations. 

### Create Data Objects <a name="section1-dataobject"></a>

1.	Click **Data Objects** tab
    <p>
     <img src="images/dataobject_1.png" width="600">
  
2.	Click **+** in *Local Data Objects* section to create data object
    <p>
     <img src="images/dataobject_2.png" width="600">

3. In the *New Data Object* screen, do the following:
    - Enter **Investment** in the **Name** box.
    - Enter **Investment** in the **Label** box.
    - Enter **Details of the investment** in the **Description** box.
    - Click **Attributes** tab.
    
    <p>
     <img src="images/dataobject_3.png" width="600">
    
4. In *Simple Attributes* section of *Attributes* tab, do the following:
    - Click **+** to create attribute.
    - Enter **Type** in the **Name** box.
    - Enter **Type** in the **Label** box.
    - Enter **Type of investment** in the **Description** box.
    
    <p>
     <img src="images/dataobject_4.png" width="600">
    
 5. Repeat the step 4 above to create more data object attributes with following details: 
    
    | Name | Label | Description | Type |
    |---|---|---| --- |
    | Country | Country | Country | String |  
    | TotalCost | Total Cost | Total cost of investment  | Number | 
    | BusinessUnit | Business Unit | Business unit or the division that is proposing the investment  | String | 
    
    <p>
     <img src="images/dataobject_5.png" width="600">
    
    - Click **Activate**
    - Click **Capital Expenditure Rules** to navigate back to the *Data Objects* page
### Expose Data Object<a name="section1-ExposeDataObject"></a>
1. In Project Details do the following to expose the Data Object to consume from Process Template later.
    - Select Project Details and scroll down to  Exposed Vocabulary.
    - Click Data Object to select the modeled data obejct.

 <img src="images/SelectDataObject.png" width="600">
 2.    In the Data Objects dialogue Select Investment dataobejct and click OK button.

 <img src="images/ConfirmDataObject.png" width="600">

 3. Click **Activate** to activate the project.
 <img src="images/ActivateProject.png" width="600">
 4. Click **Release Version** to releaes the project.
    <img src="images/Release Version.png" width="600">
 5. Update the followng to release the Project.
    - **Verison** as 1.0.0
    - **Revision** as Trial
    - **Description** "Vocabulary to create Step and Start Condition"
    - Click **Release** button
 <img src="images/Release.png" width="600">

 6. Copy the Project ID to use from the Process Template Editor
    - Go to Manage Prjects
    - Click Project Settings
    <img src="images/ProjectSettings.png" width="600">
    - Select the **ID** field from the list and click **OK** button
    <img src="images/SelectProjectId.png" width="600">
7. Copy the Project ID field and keep it in your notepad.
<img src="images/CopyProjectId.png" width="600">
### Summary<a name="Summary"></a>
Now you have modeled a Business Rules Project with a Data Object and exposed it for consuming from Process Template Editor in the next excercise.