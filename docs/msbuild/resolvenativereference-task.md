---
title: "ResolveNativeReference, tâche | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveNativeReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNativeReference task
- ResolveNativeReference task [MSBuild]
ms.assetid: 56acd101-de77-4eec-92c6-f5c6d2187579
caps.latest.revision: 9
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b0b08a9602c81e504bf2cd01d1d1ce9720dc6b2a
ms.lasthandoff: 02/22/2017

---
# <a name="resolvenativereference-task"></a>ResolveNativeReference, tâche
Résout des références natives. Implémente la classe </xref:Microsoft.Build.Tasks.ResolveNativeReference>. Cette classe prend en charge l’infrastructure .NET Framework et n’est pas destinée à être directement utilisée à partir de votre code.  
  
## <a name="task-parameters"></a>Paramètres de tâche  
 Le tableau ci-dessous décrit les paramètres de la tâche `ResolveNativeReference`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AdditionalSearchPaths`|Paramètre [String](assetId:///String?qualifyHint=False&autoUpgrade=True)`[]` obligatoire.<br /><br /> Obtient ou définit les chemins de recherche pour la résolution des identités d’assembly des références natives.|  
|`ContainedComComponents`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les composants COM de l’assembly natif.|  
|`ContainedLooseEtcFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les fichiers Etc libres répertoriés dans le manifeste natif.|  
|`ContainedLooseTlbFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les fichiers .tlb libres de l’assembly natif.|  
|`ContainedPrerequisiteAssemblies`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les assemblys qui doivent être présents pour permettre l’utilisation du manifeste.|  
|`ContainedTypeLibraries`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les bibliothèques de types de l’assembly natif.|  
|`ContainingReferenceFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient ou définit les fichiers de référence.|  
|`NativeReferences`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Obtient ou définit les références d’assemblys natifs Win32.|  
  
## <a name="remarks"></a>Notes  
 Outre les paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle-même de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez l’article [TaskExtension Base Class (Classe de base TaskExtension)](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches MSBuild](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)