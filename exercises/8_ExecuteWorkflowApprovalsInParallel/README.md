# Executing Workflow Tasks In Parallel
## Table of Contents

   -  [Overview](#overview)
   - [Model Workflow](#workflow)
   - [Execute Workflow](#excute)
   - [Summary](#summary)
   
## Overview<a name="overview"></a>
While modeling a workflow, it is a common requirment to execute approval steps in Parallel. This could be static or dynamic number of approal steps. Static number of approvals can be modeld using Workflow editor and Process Variant Editor. SAP Workflow Management now supports parallel execution of approval steps and developers can determine the number of parallel approvals during runtime and execute them in parallel. This exercise guides you how to model and execute Parallel approval steps.
## Model Workflow<a name="workflow"></a>
1. Open your Business Application Studio and Select your modeled MTA project.
2. Click View and Choose **Find Command**.

![](images/FindCommand.png)

3. Type Workflow and Choose **Create New Workflow**.
![](images/SelectWorkflow.png)

3. Select Workflow Module Name **CAPEX**.    
![](images/SelectWorkflowModule.png)

*you can ignore the optional property name space*
4. Enter the workflow Name as for eg: "CapitalExpenditureParallelApproval"
 ![](images/WorkflowName.png)
 
5. The new workflow is now available with a start and end event.
6. Update the **Subject** and **Business Key** with appropriate parameterized strings.
![](images/WorkflowProperties.png)
7. Select the Start Event and using the speed button select Referenced Subflow.
![](images/SelectReferenceSubflow.png)
8. Select Start Event and in the Properties choose **Details**.
9. Check  Configure Sample Context.
10. Click link **Create File**.
![](images/StartPayload.png)
11. In the dialgoue enter Name. for eg: CapexParallelApprovalStartPayload.
![](images/CreateNewFile.png)
12. Remove the default JSON content and copy and paste the content from .
13. Open the provided file [CapexParallelApprovalStartPayload.json.json](files/CapexParallelApprovalStartPayload.json.json) and copy the content into the open editor window. Replace Name and UserId with your name and BTP user Id.
```json
{
    "RequestId": "CAPEX_REQ_001",
    "Title": "Build mobile apps",
    "Requester": {
        "Name":"<your name>",
        "UserId":"<your userId>",
        "Comment":"Please Approve"
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
    },
    "ApprovalSteps":
     [
         {"ApprovalStep":"LocalManager"},
         {"ApprovalStep":"GroupHead"},
         {"ApprovalStep":"CFO"}
     ],
     "ApprovalHistory":
     [
          {},{},{}
     ]
   
}
```
15. Select the Referenced Subflow artifact and from Properties choose  DETAILS.
16. Click Select to choose a Workflow Definition as Referened Subflow.
    ![](images/SelectSubflow.png)
17. Expand the Workflow node and Select ApprovalStep.workflow
18. Click OK Button.
![](images/SelecRefSubflow.png)
19. Check **Propagate Principal** to enable principal propagation while creating the referenced workflow during runtime.
20. Click **Select** and from the Dialogure window choose **StartEvent1**
![](images/SelectFlowElement.png)

20. Select **Type** as Parallel.
21. Update **Collection Context Path** as ${context.ApprovalSteps}  

![](images/ParallelLooping.png)
22. Select tab **MAPPING**.
![](images/Mapping.png)
23. Under **Input Mapping** and click **Add** button five times.
Update the Source Context Path and Target Context Path as given below.

*Source Context Path is the Main workflow context and Target Context Path is the Referenced Subflow context path.**loop.counter** is a standard variable to access the index of the collection attached to the reference subflow*.
Source Context Path | Target Context Path
   --- | ---
   `${context.RequestId}` |`${context.RequestId}`
   `${context.Title}` |`${context.Title}`
   `${context.Requester}` |`${context.Requester}}`
   `${context.Investment}` |`${context.Investment}`
   `${context.ApprovalSteps[loop.counter].ApprovalStep}` |`${context.approvalstep}`

25. Under **Output Mapping** and click **Add** button.

Source Context Path | Target Context Path
   --- | ---
   `${context.History}` |`${context.ApprovalHistory[loop.counter]}`

   26. Build your MTA Project.

   ![](images/BuildMTA.png) 
   
   27. Deploy your MTA Archive. 

   ![](images/deploymta.png)

   ## Execute Workflow<a name="execute"></a>
   28.Click **Monitor Workflows - Workflow Definitions** tile to view the newly deployed workflow definition.
   ![](images/MonitorWorkflowDefinition.png)
   29. Select the newly deployed Workflow Definition.   
   30. Click **Start New Instance** action in the footer.
     ![](images/SelectWorkflowDefinition.png)
   31. Click **Start New Instance and Close**.
    ![](images/ParallelWorkflowStartPayload.png)

   32. Click **Show Instances** button to see the newly created Workflow Instance.

   ![](images/ParallelShowInstances.png)
   33. Select **EXECUTION LOG** and you can see three Referenced Subflows are started. Each Subflow is of type Approval Step and has a Workflow Task to approve.
   ![](images/ParallelWorkflowInstance.png)
  34. Navigate to Home Page and Select **My Inbox**.    
  35. Click **My Inbox** tile.
  You can see there are three tasks in your My Inbox for approvals.
  ![](images/MyInboxParallelApprovals.png)

36. You can see there are three tasks in parallel.
- Local Manager Approval
- Group Head Approval
- CFO Approval
  ![](images/ThreeTasksInParallel.png)

37. Click **Approve** to complete  all  three tasks.
38. Navigate to Home and Select **Monitor Workflow Workflow Instances** tile.
39. Add Status Filter **"Completed"**.
You can see the newly workflow instance completed and the Workflow Context Shows the History of approvals. The Execution log shows the status of three Referenced Subflow instances.
  ![](images/CompletedInstance.png)
 ## Summary<a name="summary"></a>
 Now you have learned how to configure Referenced Subflow and enable parallel approvals dynamically.

