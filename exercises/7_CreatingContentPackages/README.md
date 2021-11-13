# Creating and Consuming Process Content Packages
## Table of Contents
- [Create Workflow Management Content Package](#contentpackage)
    - [Overview](#overview)
    - [Create Content Package](#createpackage)
- [Configure and Deploy Process Variant](#configureanddeploy)
  - [Create New Process Variant](#createvariant)
  - [Configure Process Variant](#configurevariant)
  - [Configure Decision](#configuredecision)
  - [Execute and Monitor Process Variant](#monitorvariant)
  - [Live Process Insights](#liveprocessinsights)
- [Summary](#summary)
   
## Create Workflow Management  Content Package <a name="contentpackage"></a>
### Overview <a name="overview"></a>
A Workflow Managment content package consists of Process Templates, Workflows, Business Rules, Process Visibility Scenario, Multi Target Application(MTA Archive) and Sources. A developer could also attach the related documents like setup, configuration and user guides. Each of the artifact in the package can be assigned a version and revision.
### Create Content Package <a name="createpackage"></a>
1. Open your SAP BTP Cockpit at https://cockpit.hanatrial.ondemand.com/
2. Navigate to your subaccount
3. Select Services / Instances and Subscriptions
4. Click Workflow Management

![](images/btp-cockpit-2.jpg)

In the Fiori Launchpad open Manage Packages application.
Click the tile **Manage Packages**.

![](images/portal.png)

The Manage Packates application is opened. Click **Create** button.

![](images/ManagePackages.png)

A new dialogue window opens and enter the following data.

1. **Namespace** : open.sap.com
2. **Name**: capitalexpenditureapproval
3. **Revision**: 2021
4. **Short Description**: Capital expenditure approval process package including process template, business rules and process visibility content.
5. Click **Save** button.

![](images/newpackage.png)

The newly created package is now opened in the editor.
Add appropriate **Description**.

![](images/managepackageseditor.png)
The various workflow management artifacts needs to be included in this package.
1. Click tab **Artifacts**.
2. Click the **+** button.
3. Select **Add Processes**.
![](images/AddProcesses.png)

The dialogue shows all deplyoed process templates. Select **CapexApproval** and click **Select** button.
![](images/selectProcess.png)

Repeat the same for Business Rules and Process Visibility scenario.

1.Click tab **Artifacts**.  
2.Click the **+** button.  
3.Select **Add Business Rules Project**.
![](images/AddBusinessRules.png)

The dialogue shows all deplyoed Business Rules Projects.Select **Sample policies for capital expenditure approval** and click **Select** button.
![](images/SelectBusinessRules.png)

1.Click tab **Artifacts**.  
2. Click the **+** button.  
3. Select **Add Process Visiblity Scenario**.  
![](images/AddVisibilityscenario.png)

The dialogue shows all Activated Process Visibility Scenarios.Select **Capital Expenditure Approvals** and click **Select** button.
![](images/SelectVisibilityScenario.png)
1. Enter Revision as **2021**
2. Enter Version as **1.0.0**
3. Click **Save** button to save the package.
![](images/SavePackage.png)

*Your content package is ready to consume now or you could export your content package to transport the content to another BTP subaccount*.

Click **Home** Button and navigate to the home page.
![](images/ManagePackagesToHome.png)

## Configure and Deploy Process Variants <a name="configureanddeploy"></a>
1. Click **Process Flexibility** tile to configure and deploy a process variant.
![](images/ProcessFlexiblityCockpitTile.png)

*Process Fleixiblity Cockpit enable Process experts to configure process variants, manage decisions and  visibility scenarios. It is a single page enable process owners to manage their proccess variants and monitor the performance*.
### Create New Process Variant<a name="createvariant"></a>
You can see the content package **capitalexpenditureapproval** created in the Manage Packages Application available now.Click the tile **capitalexpenditureapproval**.
![](images/SelectContentPackage2.png)
You can see the **Process Flexibility Cockpit** with all the artifacts in the content package.Since there is no Process Variants created and activated, All the tiles show the packaged artifacts.

Click the action **New Process Variant**.
![](images/CreateNewProcessVariant.png)
A new dialogue window open to provide the proess variant name.
1. Select the Process **CapexApproval**  from the dropdown as Process Template.
2. Enter a **name** to the process variant for eg: capitalexpenditureapproval.
3. Click **Create** action button.
![](images/NewProcessVariant.png)

The new Process Variant is available in the Process Variants tile with **draft** state.
![](images/SelectProcessVariants.png)
Click the header area of  **Process Variants** tile.
### Configure Process Variant <a name="configurevariant"></a>
A process variant has default steps configured while creating the process template and it is possible to modify or add new steps.  
Click the Process Variant **capitalexpenditureapproval** to navigate to process variant editor.
![](images/SelectProcessVariant.png)
*The Process Variant Editor is available now to configure a new variant. It shows the default variant and steps in the process template*.

*You can add new approval steps and configure. The **Available Steps**  Palette shows the available steps to consume in a process variant. The default variant has two steps. The step details shows possilbe configurations you can do while configuring a step*.

- Select **Step Conditions** tab to configure a step condition.
- Select **Investment.Total Cost** from the drop down.
- Select **>=**as the operator.
- Enter **10000** as the Total Cost value. 

*This configuration will enable you to execute this Process Variant if the Total Cost of investment is greater than or equal to 10000*.
![](images/ProcessVariantStartCondition.png)
Select **Group Head Approval** Step to configure step conditions.
- Select **Step Conditions** tab.
- Select **Investment.Total Cost** from the drop down.
- Select **>=**as the operator.
- Enter **30000** as the Total Cost value.
![](images/GroupHeadStepCondition.png)
**Drag and Drop** Approval Step from palette to Process Variant. The newly added Approval Step part of the Process Variant now.
![](images/DragAndDropProcessStep.png)
 *It is possilbe to execute multiple step parallelly. You need to drag and drop the process step on an exisiting step so that two steps execute parallely*.

 Select the newly added step and change the Step **Name** to CFO.
 ![](images/StepRenameCFO.png)

 Select the **Details** tab.
 Enter the **approvalstep** as "CFO".
 ![](images/StepPropertyCFO.png)

 *This is a step attribute you have configured while creating the  process template .It is used while determining the approver using a business rule*.

 
 Select the **Step Conditions** tab.
 Select **Investment.Total Cost** from the drop down.
- Select **>=**as the operator.
- Enter **50000** as the Total Cost value.
- Click **Activate** button.
![](images/CFOStepCondition.png)


Successful activation of the process variant will display a toast message. A new workflow definition is deployed in to your subaccount. The Start and Step conditions are part of a generated Business Rules Project in your sub account.

![](images/ActivationMessage.png)

### Execute and Montior Process Variant <a name="monitorvariant"></a>
In this section you will create an instance of the process variant you have activated. The process variant has three approval steps and approvers are determined using the decision which you have modified in the previous section. 

Click **Monitor Workflow - Workflow Definition** Tile to view the newly deployed Workflow definition.

![](images/MonitorWorkflowsDefinitions.png)

You can see the newly activated Process Variant **capitalexpenditureapproval** deployed to your account. You can also see the approval steps you have developed and deployed to your account. One more wokflow with name **CapexApproval_Leading Workflow** got generated. This Workflow is managign the Start and Step conditions you have modled in the previous steps.

Select the workflow definition **CapexApproval_Leading Workflow**   and click **Start New Instance**.
![](images/LeadingWorkflow.png)
Delete the sample JSON from the dialogue.

**Copy  and Paste** the below JSON  content.

```json

   {
    "RequestId": "CAPEX_REQ_001",
    "Title": "Build mobile apps",
    "Requester": {
        "Name": "Your Name",
        "UserId": "Your SAP BTP Trial User Id",
        "Comment": "Please Approve"
    },
    "Investment": {
        "Type": "Software",
        "Description": "Provide a fresh experience for our customers by providing new apps for our services",
        "TotalCost": 15000,
        "CAPEX": 10000,
        "OPEX": 5000,
        "ROI": 5,
        "Currency": "EUR",
        "BusinessUnit": "Purchasing",
        "Country": "Germany"
    }

```
Change your **Name** and **UserId** under Requester.
UserId should be your BTP trial accont user id.
The Total Cost determine the process variant to be used and the number of approval steps to be used in the workflow instance.
Click **Start New Instance and Close**.
![](images/startNewInstanceAndClose.png)
A new workflow instance of your newly deployed process variant got created.

Click **Show Instances** button to see the newly created workflow instance.
![](images/ShowInstances.png)
The Monitor Workflow Instnaces Application will show the root workflow instnace. 
Click **EXECUTION LOG** to see the detials of the activites executed so far.
The activity Reference subflow **"Call Variant"** is started shows the instnace Id of the workflow approval step.

Click on the link **Instance Id** to navigate to the Process Variant.

![](images/LeadingWorkflowInstance.png)
The child workflow instance **"Two Step Approval"** is displayed now. This is the Process Variant you have configured and deployed.

Click on the link **Instance Id** to navigate to the Approval Step.
![](images/ProcessVariantInstance.png)
The child workflow instance **"ApprovalStep"** is displayed now.
Click tab **EXECUTION LOG**. It shows the Group Head approval task is ready and assigned to your BTP trial user id.
![](images/GroupHeadApprovalInstance.png)
Navigate to **Home** screen and click **My Inbox** application.The newly created approval task is available to you as Group Head. 
![](images/MyInbox.png)

Select the Task and click **Approve** button to complete. You may also add a Comment in comment section.
![](images/ApproveGroupHead.png)

Click **REFRESH** button to get the next approval task. This will update My Inbox with the next approval task.

![](images/refresh.png)

Select the approval task Local Manager approval and click **Approve** button. You may add comments in theComments section.

![](images/ApproveLocalManager.png)

Click **REFRESH** button to get the next approval task. This will update My Inbox with the next approval task.

![](images/refresh.png)

Select the approval task CFO approval and click **Approve** button. You may add comments in the Comments section.

![](images/ApproveCFO.png)

### Live Process Insights <a name="liveprocessinsights"></a>
SAP Workflow Management provides real time visibility into processes and deployed workflows. Process owners and Process operators can get insight into their Process variants. 
Navigate to **Process Flexiblity Cockpit** and click on **Live Process Insights**.

![](images/LiveProcessInsightsTile.png)
You will see status of your Workflow Instance including some key performance indicators you have modeled in the previous exercise.
![](images/processvisibilityworkspace.png)

## Summary <a name="summary"></a>
In this excercise you have learned how to 
* Create a content package.
* Create a process variant.
* Configure a process variant and activate.
* Execute and Monitor Process Variants.
* Live Process Insights.