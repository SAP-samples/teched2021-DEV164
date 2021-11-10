# Model Businenss Rules Vocabulary 

## Table of Contents

## Table of Contents
- [Author, Activate and Deploy Business Rules](#section1)
    - [Overview](#section1-overview)
    - [Create Project](#section1-createproject)
    - [Create Data Object](#section1-dataobject)
    - [Summary](#summary)
   




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
