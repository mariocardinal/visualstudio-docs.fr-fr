---
title: "Comment : référencer le nom ou l’emplacement du fichier projet | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
caps.latest.revision: "13"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 9186b98b482b101254e70def9285d9bbad2ca254
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Comment : référencer le nom ou l'emplacement du fichier projet
Vous pouvez utiliser le nom ou l’emplacement du projet dans le fichier projet sans avoir à créer votre propre propriété. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fournit des propriétés réservées qui référencent le nom du fichier projet et d’autres propriétés associées au projet. Pour plus d’informations sur les propriétés réservées, consultez l’article [Propriétés réservées et connues de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="using-the-msbuildprojectname-property"></a>Utilisation de la propriété MSBuildProjectName  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fournit quelques propriétés réservées que vous pouvez utiliser dans vos fichiers projet sans les définir à chaque fois. Par exemple, la propriété réservée `MSBuildProjectName` fournit une référence au nom du fichier projet.  
  
#### <a name="to-use-the-msbuildprojectname-property"></a>Pour utiliser la propriété MSBuildProjectName  
  
-   Référencez la propriété dans le fichier projet avec la notation $(), comme vous le feriez avec n’importe quelle propriété. Exemple :  
  
    ```xml  
    <CSC Sources = "@(CSFile)"   
        OutputAssembly = "$(MSBuildProjectName).exe"/>  
    </CSC>  
    ```  
  
 L’un des avantages liés à l’utilisation d’une propriété réservée est que les modifications apportées au nom du fichier projet sont incorporées automatiquement. À la prochaine génération du projet, le fichier de sortie dispose du nouveau nom sans aucune intervention supplémentaire de votre part.  
  
> [!NOTE]
>  Les propriétés réservées ne peuvent pas être redéfinies dans le fichier projet.  
  
## <a name="example"></a>Exemple  
 L’exemple de fichier projet suivant référence le nom du projet en tant que propriété réservée pour spécifier le nom de la sortie.  
  
```xml  
<Project xmlns="http://scheams.microsoft.com/developer/msbuild/2003"   
    DefaultTargets = "Compile">  
  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using  
        input files of type CSFile -->  
        <CSC Sources = "@(CSFile)"  
            OutputAssembly = "$(MSBuildProjectName).exe" >  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the project -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
[MSBuild](../msbuild/msbuild.md)  
 [Propriétés réservées et connues de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)