---
title: "Tâches inline MSBuild | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
caps.latest.revision: 20
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
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: 6153ab5924f66d13e2c0664ed652f8eee6f91e4c
ms.lasthandoff: 02/22/2017

---
# <a name="msbuild-inline-tasks"></a>Tâches inline MSBuild
Vous créez généralement des tâches MSBuild en compilant une classe qui implémente l’interface <xref:Microsoft.Build.Framework.ITask>. Pour plus d’informations, consultez l’article [Tâches MSBuild](../msbuild/msbuild-tasks.md).  
  
 À compter du .NET Framework version 4, vous pouvez créer des tâches inline dans le fichier projet. Vous n’êtes pas obligé de créer un assembly distinct pour héberger la tâche. Cela facilite le suivi du code source et le déploiement de la tâche. Le code source est intégré au script.  
  
## <a name="the-structure-of-an-inline-task"></a>Structure d’une tâche inline  
 Une tâche inline est contenue dans un élément [UsingTask](../msbuild/usingtask-element-msbuild.md). La tâche inline et l’élément `UsingTask` qui la contient sont généralement inclus dans un fichier .targets et importés dans d’autres fichiers projet selon les besoins. Voici une tâche inline de base. Notez qu’elle n’a aucun effet.  
  
```xml  
<Project ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- This simple inline task does nothing. -->  
  <UsingTask  
    TaskName="DoNothing"  
    TaskFactory="CodeTaskFactory"  
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v12.0.dll" >  
    <ParameterGroup />  
    <Task>  
      <Reference Include="" />  
      <Using Namespace="" />  
      <Code Type="Fragment" Language="cs">  
      </Code>  
    </Task>  
  </UsingTask>  
</Project>  
```  
  
 L’élément `UsingTask` dans l’exemple a trois attributs qui décrivent la tâche et la fabrique de tâches inline qui la compile.  
  
-   L’attribut `TaskName` nomme la tâche, dans le cas présent `DoNothing`.  
  
-   L’attribut `TaskFactory` nomme la classe qui implémente la fabrique de tâches inline.  
  
-   L’attribut `AssemblyFile` indique l’emplacement de la fabrique de tâches inline. Vous pouvez également utiliser l’attribut `AssemblyName` pour spécifier le nom qualifié complet de la classe de fabrique de tâches inline, qui se trouve généralement dans le global assembly cache (GAC).  
  
 Les éléments restants de la tâche `DoNothing` sont vides et fournis pour illustrer l’ordre et la structure d’une tâche inline. Un exemple plus pertinent est présenté plus loin dans cette rubrique.  
  
-   L’élément `ParameterGroup` est facultatif. Quand il est spécifié, il déclare les paramètres de la tâche. Pour plus d’informations sur les paramètres d’entrée et de sortie, consultez « Paramètres d’entrée et de sortie » plus loin dans cette rubrique.  
  
-   L’élément `Task` décrit et contient le code source de la tâche.  
  
-   L’élément `Reference` spécifie des références aux assemblys .NET que vous utilisez dans votre code. Cela équivaut à ajouter une référence à un projet dans Visual Studio. L’attribut `Include` spécifie le chemin de l’assembly référencé.  
  
-   L’élément `Using` répertorie les espaces de noms auxquels vous souhaitez accéder. Cela ressemble à l’instruction `Using` en Visual C#. L’attribut `Namespace` spécifie l’espace de noms à inclure.  
  
 Les éléments `Reference` et `Using` sont indépendants du langage. Les tâches inline peuvent être écrites dans n’importe quel langage .NET CodeDom pris en charge, par exemple Visual Basic ou Visual C#.  
  
> [!NOTE]
>  Les éléments contenus dans l’élément `Task` sont propres à la fabrique de tâches, dans le cas présent la fabrique de tâches de code.  
  
### <a name="code-element"></a>Élément Code  
 Le dernier élément enfant de l’élément `Task` est l’élément `Code`. L’élément `Code` contient ou identifie le code à compiler dans une tâche. Ce que vous placez dans l’élément `Code` dépend de la façon dont vous souhaitez écrire la tâche.  
  
 L’attribut `Language` spécifie le langage dans lequel votre code est écrit. Les valeurs acceptables sont `cs` pour C# et `vb` pour Visual Basic.  
  
 L’attribut `Type` spécifie le type de code qui se trouve dans l’élément `Code`.  
  
-   Si la valeur de `Type` est `Class`, l’élément `Code` contient du code pour une classe qui dérive de l’interface <xref:Microsoft.Build.Framework.ITask>.  
  
-   Si la valeur de `Type` est `Method`, le code définit une substitution de la méthode `Execute` de l’interface <xref:Microsoft.Build.Framework.ITask>.  
  
-   Si la valeur de `Type` est `Fragment`, le code définit le contenu de la méthode `Execute`, mais pas la signature ou l’instruction `return`.  
  
 Le code proprement dit apparaît généralement entre un marqueur `<![CDATA[` et un marqueur `]]>`. Comme le code se trouve dans une section CDATA, vous n’avez pas à vous soucier de l’échappement des caractères réservés, tels que « \< » ou « > ».  
  
 Vous pouvez également utiliser l’attribut `Source` de l’élément `Code` pour spécifier l’emplacement d’un fichier qui contient le code de votre tâche. Le code dans le fichier source doit être du type spécifié par l’attribut `Type`. Si l’attribut `Source` est présent, la valeur par défaut de `Type` est `Class`. Si `Source` est absent, la valeur par défaut est `Fragment`.  
  
> [!NOTE]
>  Quand vous définissez la classe de la tâche dans le fichier source, le nom de classe doit correspondre à l’attribut `TaskName` de l’élément [UsingTask](../msbuild/usingtask-element-msbuild.md) correspondant.  
  
## <a name="hello-world"></a>Hello World  
 Voici une tâche inline plus robuste. La tâche HelloWorld affiche « Hello, world! » sur l’appareil de journalisation des erreurs par défaut, qui est généralement la console système ou la fenêtre **Sortie** de Visual Studio. L’élément `Reference` dans l’exemple est fourni uniquement à titre d’illustration.  
  
```xml  
<Project ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- This simple inline task displays "Hello, world!" -->  
  <UsingTask  
    TaskName="HelloWorld"  
    TaskFactory="CodeTaskFactory"  
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
    <ParameterGroup />  
    <Task>  
      <Reference Include="System.Xml.dll"/>  
      <Using Namespace="System"/>  
      <Using Namespace="System.IO"/>  
      <Code Type="Fragment" Language="cs">  
<![CDATA[  
// Display "Hello, world!"  
Log.LogError("Hello, world!");  
]]>  
      </Code>  
    </Task>  
  </UsingTask>  
</Project>  
```  
  
 Vous pouvez enregistrer la tâche HelloWorld dans un fichier nommé HelloWorld.targets, puis l’appeler à partir d’un projet en procédant comme suit.  
  
```xml  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <Import Project="HelloWorld.targets" />  
  <Target Name="Hello">  
    <HelloWorld />  
  </Target>  
</Project>  
```  
  
## <a name="input-and-output-parameters"></a>Paramètres d’entrée et de sortie  
 Les paramètres de tâche inline sont des éléments enfants d’un élément `ParameterGroup`. Chaque paramètre prend le nom de l’élément qui le définit. Le code suivant définit le paramètre `Text`.  
  
```xml  
<ParameterGroup>  
    <Text />  
</ParameterGroup>  
```  
  
 Les paramètres peuvent avoir un ou plusieurs de ces attributs :  
  
-   `Required` est un attribut facultatif qui est `false` par défaut. Si cet attribut est `true`, le paramètre est obligatoire et vous devez lui affecter une valeur avant d’appeler la tâche.  
  
-   `ParameterType` est un attribut facultatif qui est `System.String` par défaut. Vous pouvez lui affecter n’importe quel type qualifié complet qui est un élément ou une valeur pouvant être converti vers et à partir d’une chaîne à l’aide de System.Convert.ChangeType. (En d’autres termes, tout type qui peut être passé à et depuis une tâche externe.)  
  
-   `Output` est un attribut facultatif qui est `false` par défaut. Si cet attribut est `true`, vous devez affecter une valeur au paramètre avant le retour de la méthode Execute.  
  
 Par exemple :  
  
```xml  
<ParameterGroup>  
    <Expression Required="true" />  
      <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />  
    <Tally ParameterType="System.Int32" Output="true" />  
</ParameterGroup>  
```  
  
 définit ces trois paramètres :  
  
-   `Expression` est un paramètre d’entrée obligatoire de type System.String.  
  
-   `Files` est un paramètre d’entrée de liste d’éléments obligatoire.  
  
-   `Tally` est un paramètre de sortie de type System.Int32.  
  
 Si l’élément `Code` a un attribut `Type` égal à `Fragment` ou `Method`, des propriétés sont créées automatiquement pour chaque paramètre. Dans le cas contraire, les propriétés doivent être déclarées explicitement dans le code source de la tâche, et elles doivent correspondre exactement à leurs définitions de paramètres.  
  
## <a name="example"></a>Exemple  
 La tâche inline suivante remplace chaque occurrence d’un jeton dans le fichier spécifié par la valeur donnée.  
  
```xml  
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="12.0">  
  
  <UsingTask TaskName="TokenReplace" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v12.0.dll">  
    <ParameterGroup>  
      <Path ParameterType="System.String" Required="true" />  
      <Token ParameterType="System.String" Required="true" />  
      <Replacement ParameterType="System.String" Required="true" />  
    </ParameterGroup>  
    <Task>  
      <Code Type="Fragment" Language="cs"><![CDATA[  
string content = File.ReadAllText(Path);  
content = content.Replace(Token, Replacement);  
File.WriteAllText(Path, content);  
  
]]></Code>  
    </Task>  
  </UsingTask>  
  
  <Target Name='Demo' >  
    <TokenReplace Path="C:\Project\Target.config" Token="$MyToken$" Replacement="MyValue"/>  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches MSBuild](../msbuild/msbuild-tasks.md)   
 [Procédure pas à pas : création d’une tâche inline](../msbuild/walkthrough-creating-an-inline-task.md)
