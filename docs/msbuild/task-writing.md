---
title: Task Writing | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
caps.latest.revision: 19
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: e9757d10249e3a8d6b06804623a06ab971e86d89
ms.contentlocale: fr-fr
ms.lasthandoff: 08/30/2017

---
# <a name="task-writing"></a>Task Writing
Tasks provide the code that runs during the build process. Tasks are contained in targets. A library of typical tasks is included with [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], and you can also create your own tasks. For more information about the library of tasks that are included with [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], see [Task Reference](../msbuild/msbuild-task-reference.md).  
  
## <a name="tasks"></a>Tasks  
 Examples of tasks include [Copy](../msbuild/copy-task.md), which copies one or more files, [MakeDir](../msbuild/makedir-task.md), which creates a directory, and [Csc](../msbuild/csc-task.md), which compiles [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] source code files. Each task is implemented as a .NET class that implements the <xref:Microsoft.Build.Framework.ITask> interface, which is defined in the Microsoft.Build.Framework.dll assembly.  
  
 There are two approaches you can use when implementing a task:  
  
-   Implement the <xref:Microsoft.Build.Framework.ITask> interface directly.  
  
-   Derive your class from the helper class, <xref:Microsoft.Build.Utilities.Task>, which is defined in the Microsoft.Build.Utilities.dll assembly. Task implements ITask and provides default implementations of some ITask members. Additionally, logging is easier.  
  
 In both cases, you must add to your class a method named `Execute`, which is the method that is called when the task runs. This method takes no parameters and returns a `Boolean` value: `true` if the task succeeded or `false` if it failed. The following example shows a task that performs no action and returns `true`.  
  
```csharp
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
        }  
    }  
}  
```  
  
 The following project file runs this task:  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 When tasks run, they can also receive inputs from the project file if you create .NET properties on the task class. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sets these properties immediately before calling the task's `Execute` method. To create a string property, use task code such as:  
  
```csharp
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
         }  
  
        private string myProperty;  
        public string MyProperty  
        {  
            get { return myProperty; }  
            set { myProperty = value; }  
        }  
    }  
}  
```  
  
 The following project file runs this task and sets `MyProperty` to the given value:  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## <a name="registering-tasks"></a>Registering Tasks  
 If a project is going to run a task, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] must know how to locate the assembly that contains the task class. Tasks are registered using the [UsingTask Element (MSBuild)](../msbuild/usingtask-element-msbuild.md).  
  
 The [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] file Microsoft.Common.Tasks is a project file that contains a list of `UsingTask` elements that register all the tasks that are supplied with [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. This file is automatically included when building every project. If a task that is registered in Microsoft.Common.Tasks is also registered in the current project file, the current project file takes precedence; that is, you can override a default task with your own task that has the same name.  
  
> [!TIP]
>  You can see a list of the tasks that are supplied with [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] by viewing the contents of Microsoft.Common.Tasks.  
  
## <a name="raising-events-from-a-task"></a>Raising Events from a Task  
 If your task derives from the <xref:Microsoft.Build.Utilities.Task> helper class, you can use any of the following helper methods on the <xref:Microsoft.Build.Utilities.Task> class to raise events that will be caught and displayed by any registered loggers:  
  
```csharp
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 If your task implements <xref:Microsoft.Build.Framework.ITask> directly, you can still raise such events but you must use the IBuildEngine interface. The following example shows a task that implements ITask and raises a custom event:  
  
```csharp
public class SimpleTask : ITask  
{  
    private IBuildEngine buildEngine;  
    public IBuildEngine BuildEngine  
    {  
        get{ return buildEngine; }  
        set{ buildEngine = value; }  
    }  
  
    public override bool Execute()  
    {  
        TaskEventArgs taskEvent =  
            new TaskEventArgs(BuildEventCategory.Custom,  
            BuildEventImportance.High, "Important Message",  
           "SimpleTask");  
        BuildEngine.LogBuildEvent(taskEvent);  
        return true;  
    }  
}  
```  
  
## <a name="requiring-task-parameters-to-be-set"></a>Requiring Task Parameters to be Set  
 You can mark certain task properties as "required" so that any project file that runs the task must set values for these properties or the build fails. Apply the `[Required]` attribute to the .NET property in your task as follows:  
  
```csharp
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 The `[Required]` attribute is defined by <xref:Microsoft.Build.Framework.RequiredAttribute> in the <xref:Microsoft.Build.Framework> namespace.  
  
## <a name="example"></a>Example  
  
### <a name="description"></a>Description  
 This following [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] class demonstrates a task deriving from the <xref:Microsoft.Build.Utilities.Task> helper class. This task returns `true`, indicating that it succeeded.  
  
### <a name="code"></a>Code  
  
```csharp
using System;  
using Microsoft.Build.Utilities;  
  
namespace SimpleTask1  
{  
    public class SimpleTask1: Task  
    {  
        public override bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## <a name="example"></a>Example  
  
### <a name="description"></a>Description  
 This following [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] class demonstrates a task implementing the <xref:Microsoft.Build.Framework.ITask> interface. This task returns `true`, indicating that it succeeded.  
  
### <a name="code"></a>Code  
  
```csharp
using System;  
using Microsoft.Build.Framework;  
  
namespace SimpleTask2  
{  
    public class SimpleTask2: ITask  
    {  
        //When implementing the ITask interface, it is necessary to  
        //implement a BuildEngine property of type  
        //Microsoft.Build.Framework.IBuildEngine. This is done for  
        //you if you derive from the Task class.  
        private IBuildEngine buildEngine;  
        public IBuildEngine BuildEngine  
        {  
            get  
            {  
                return buildEngine;  
            }  
            set  
            {  
                buildEngine = value;  
            }  
         }  
  
        // When implementing the ITask interface, it is necessary to  
        // implement a HostObject property of type Object.  
        // This is done for you if you derive from the Task class.  
        private Object hostObject;  
        public Object HostObject  
        {  
            get  
            {  
                return hostObject;  
            }  
  
            set  
            {  
                hostObject = value;  
            }  
        }  
  
        public bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## <a name="example"></a>Example  
  
### <a name="description"></a>Description  
 This [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] class demonstrates a task that derives from the <xref:Microsoft.Build.Utilities.Task> helper class. It has a required string property, and raises an event that is displayed by all registered loggers.  
  
### <a name="code"></a>Code  
 [!code-csharp[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]  
  
## <a name="example"></a>Example  
  
### <a name="description"></a>Description  
 The following example shows a project file invoking the previous example task, SimpleTask3.  
  
### <a name="code"></a>Code  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>See Also  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)
