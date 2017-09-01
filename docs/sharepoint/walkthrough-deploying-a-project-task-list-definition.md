---
title: 'Walkthrough: Deploying a Project Task List Definition | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.prod: visual-studio-dev14
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
ms.assetid: 18b62016-ed30-4dd1-9dfc-0d7e82c6767f
caps.latest.revision: 34
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 1e0f260d1f814a2b2a3396ece8a2505561ecbbfd
ms.contentlocale: fr-fr
ms.lasthandoff: 08/30/2017

---
# <a name="walkthrough-deploying-a-project-task-list-definition"></a>Walkthrough: Deploying a Project Task List Definition
  This walkthrough shows you how to use [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] to create, customize, debug, and deploy a SharePoint list to track project tasks.  
  
 This walkthrough illustrates the following tasks:  
  
-   [Creating a SharePoint List](#CreatingListDef).  
  
-   [Creating a SharePoint List](#CreatingListDef).  
  
-   [Adding an Event Receiver](#AddEventRcvr).  
  
-   [Customizing the Project Task List Feature](#CustomizeFeature).  
  
-   [Building and Testing the Project Task List](#BuildTest).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisites  
 You need the following components to complete this walkthrough:  
  
-   Supported editions of Microsoft Windows and SharePoint. For more information, see [Requirements for Developing SharePoint Solutions](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)] or an edition of Visual Studio Application Lifecycle Management (ALM).  
  
##  <a name="CreatingListDef"></a> Creating a SharePoint List  
 Create a SharePoint list project and associate the list definition with tasks.  
  
#### <a name="to-create-a-sharepoint-list-project"></a>To create a SharePoint list project  
  
1.  Open the **New Project** dialog box, expand the **SharePoint** node, and then choose the **2010** node.  
  
2.  In the **Templates** pane, choose the **SharePoint 2010 Project** template, name the project **ProjectTaskList**, and then choose the **OK** button.  
  
     The **SharePoint Customization Wizard** appears.  
  
3.  Specify the local SharePoint site that you use for debugging, choose the **Deploy as a farm solution** option button, and then choose the **Finish** button.  
  
4.  Open the shortcut menu for the project, and then choose **Add**, **New Item**.  
  
5.  In the **Templates** pane, choose the **List** template, and then choose the **Add** button.  
  
     The **SharePoint Customization Wizard** appears.  
  
6.  In the **What name do you want to display for your list?** box, enter **Project Task List**.  
  
7.  Choose the **Create a non-customizable list based on an existing list type of** option button, and then, in its list, choose **Tasks**, and then choose the **Finish** button.  
  
     The list, feature, and package appear in **Solution Explorer**.  
  
##  <a name="AddEventRcvr"></a> Adding an Event Receiver  
 In the task list, you can add an event receiver that automatically sets the due date and description of the task. The following procedure adds a simple event handler to the list instance as an event receiver.  
  
#### <a name="to-add-an-event-receiver"></a>To add an event receiver  
  
1.  Open the shortcut menu for the project node, choose **Add**, and then choose **New Item**.  
  
2.  In the list of SharePoint templates, choose the **Event Receiver** template, and then name it **ProjectTaskListEventReceiver**.  
  
     The **SharePoint Customization Wizard** appears.  
  
3.  On the **Choose Event Receiver Settings** page, choose **List Item Events** as the event receiver type in the **What type of event receiver do you want** list.  
  
4.  In the **What item should be the event source** list, choose **Tasks**.  
  
5.  In the list of events to handle, select the check box next to **An item was added**, and then choose the **Finish** button.  
  
     A new event receiver node is added to the project with a code file that is named **ProjectTaskListEventReceiver**.  
  
6.  Add code to the `ItemAdded` method in the **ProjectTaskListEventReceiver** code file. Each time a new task is added, a default due date and a description is added to the task. The default due date is July 1, 2009.  
  
     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]  [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]  
  
##  <a name="CustomizeFeature"></a> Customizing the Project Task List Feature  
 When you create a SharePoint solution, Visual Studio automatically creates features for the default project items. You can customize the project task list settings for the SharePoint site by using the Feature Designer.  
  
#### <a name="to-customize-the-project-task-list-feature"></a>To customize the project task list feature  
  
1.  In **Solution Explorer**, expand **Features**.  
  
2.  Open the shortcut menu for **Feature1**, and then choose **View Designer**.  
  
3.  In the **Title** box, enter **Project Task List Feature**.  
  
4.  In the **Scope** list, choose **Web**.  
  
5.  In the **Properties** window, enter **1.0.0.0** as the value for the **Version** property.  
  
##  <a name="CustomizePackage"></a> Customizing the Project Task List Package  
 When you create a SharePoint project, Visual Studio automatically adds the features that contain the default project items to the package. You can customize the project task list settings for the SharePoint site by using the Package Designer.  
  
#### <a name="to-customize-the-project-task-list-package"></a>To customize the project task list package  
  
1.  In **SolutionExplorer**, open the shortcut menu for **Package**, and then choose **View Designer**.  
  
2.  In the **Name** box, enter **ProjectTaskListPackage**.  
  
3.  Select the **Reset Web Server** check box.  
  
##  <a name="BuildTest"></a> Building and Testing the Project Task List  
 When you run the project, the SharePoint site opens. However, you must manually navigate to the location of the task list.  
  
#### <a name="to-test-the-project-task-list"></a>To test the project task list  
  
1.  Choose the F5 key to build and deploy your project task list.  
  
     The SharePoint site opens.  
  
2.  Choose the **Home** tab.  
  
3.  In the left sidebar, choose the **Project Task List** link.  
  
     The Project Task List page appears.  
  
4.  In the **List Tools** tab, choose the **Items** tab.  
  
5.  In the **Items** group, choose the **New Item** button.  
  
6.  In the **Title** text box, enter **Task1**.  
  
7.  Choose the **Save** button.  
  
     After the site is refreshed, the **Task1** task appears with a due date of 7/1/2009.  
  
8.  Choose **Task1**.  
  
     The detailed view of the task appears, and the description shows "This is a critical task."  
  
##  <a name="Deploy"></a> Deploying the Project Task List  
 After you build and test the project task list, you can deploy it to the *local system* or a *remote system*. The local system is the same computer on which you developed the solution, whereas a remote system is a different computer.  
  
#### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>To deploy the project task list to the local system  
  
1.  On the Visual Studio menu bar, choose **Build**, **Deploy Solution**.  
  
     Visual Studio recycles the IIS application pool, retracts any existing versions of the solution, copies the solution package (.wsp) file to SharePoint, and then activates its features. You can now use the solution in SharePoint. For more information about deployment configuration steps, see [How to: Edit a SharePoint Deployment Configuration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).  
  
#### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>To deploy the project task list to a remote system  
  
1.  On the Visual Studio menu bar, choose **Build**, **Publish**.  
  
2.  In the **Publish** dialog box, choose the **Publish to File System** option button.  
  
     You can change the target location in the **Publish** dialog box by choosing the ellipsis button ![Ellipsis Icon](../sharepoint/media/ellipsisicon.gif "Ellipsis Icon") and then navigating to another location.  
  
3.  Choose the **Publish** button.  
  
     A .wsp file is created for the solution.  
  
4.  Copy the .wsp file to the remote SharePoint system.  
  
5.  Use the PowerShell `Add-SPUserSolution` command to install the package on the remote SharePoint installation. (For farm solutions, use the `Add-SPSolution` command.)  
  
     For example, `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.  
  
6.  Use the PowerShell `Install-SPUserSolution` command to deploy the solution. (For farm solutions, use the `Install-SPSolution` command.)  
  
     For example, `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.  
  
     For more information about remote deployment, see [Using Solutions](http://go.microsoft.com/fwlink/?LinkId=217680) and [Adding and Deploying Solutions with PowerShell in SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=217682).  
  
## <a name="next-steps"></a>Next Steps  
 You can learn more about how to customize and deploy SharePoint solutions from the following topics:  
  
-   [Walkthrough: Create a Site Column, Content Type, and List for SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)  
  
-   [How to: Create an Event Receiver](../sharepoint/how-to-create-an-event-receiver.md)  
  
-   [Windows PowerShell for SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=217684)  
  
## <a name="see-also"></a>See Also  
 [Packaging and Deploying SharePoint Solutions](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  