---
title: "Comment : spécifier la cible à générer en premier | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
caps.latest.revision: 17
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
ms.sourcegitcommit: 3ba7680d46345f2b49019659c715cfb418933d39
ms.openlocfilehash: 401db77b47014ad3330c0a78acf648605a2c3278
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-specify-which-target-to-build-first"></a>Comment : spécifier la cible à générer en premier
Un fichier projet peut contenir un ou plusieurs éléments `Target` qui définissent le mode de génération du projet. Le moteur [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) génère le premier projet trouvé, et toutes les dépendances, à moins que le fichier projet ne contienne un attribut `DefaultTargets`, un attribut `InitialTargets` ou qu’une cible ne soit spécifiée sur la ligne de commande à l’aide du commutateur **/target**.  
  
## <a name="using-the-initialtargets-attribute"></a>Utilisation de l’attribut InitialTargets  
 L’attribut `InitialTargets` de l’élément `Project` spécifie une cible qui est exécutée en premier, même si des cibles sont spécifiées sur la ligne de commande ou dans l’attribut `DefaultTargets`.  
  
#### <a name="to-specify-one-initial-target"></a>Pour spécifier une cible initiale  
  
-   Spécifiez la cible par défaut dans l’attribut `InitialTargets` de l’élément `Project`. Exemple :  
  
     `<Project InitialTargets="Clean">`  
  
 Vous pouvez spécifier plusieurs cibles initiales dans l’attribut `InitialTargets` en classant les cibles dans l’ordre et en utilisant un point-virgule pour séparer chaque cible. Les cibles de la liste seront exécutées séquentiellement.  
  
#### <a name="to-specify-more-than-one-initial-target"></a>Pour spécifier plusieurs cibles initiales  
  
-   Répertoriez les cibles initiales, séparées par des points-virgules, dans l’attribut `InitialTargets` de l’élément `Project`. Par exemple, pour exécuter la cible `Clean`, puis la cible `Compile`, tapez :  
  
     `<Project InitialTargets="Clean;Compile">`  
  
## <a name="using-the-defaulttargets-attribute"></a>Utilisation de l’attribut DefaultTargets  
 L’attribut `DefaultTargets` de l’élément `Project` spécifie la ou les cibles qui sont générées si une cible n’est pas spécifiée explicitement sur la ligne de commande. Si des cibles sont spécifiées dans les deux attributs `InitialTargets` et `DefaultTargets` et qu’aucune cible n’est spécifiée sur la ligne de commande, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] exécute les cibles spécifiées dans l’attribut `InitialTargets` suivies par les cibles spécifiées dans l’attribut `DefaultTargets`.  
  
#### <a name="to-specify-one-default-target"></a>Pour spécifier une cible par défaut  
  
-   Spécifiez la cible par défaut dans l’attribut `DefaultTargets` de l’élément `Project`. Exemple :  
  
     `<Project DefaultTargets="Compile">`  
  
 Vous pouvez spécifier plusieurs cibles par défaut dans l’attribut `DefaultTargets` en classant les cibles dans l’ordre et en utilisant un point-virgule pour séparer chaque cible. Les cibles de la liste seront exécutées séquentiellement.  
  
#### <a name="to-specify-more-than-one-default-target"></a>Pour spécifier plusieurs cibles par défaut  
  
-   Répertoriez les cibles par défaut, séparées par des points-virgules, dans l’attribut `DefaultTargets` de l’élément `Project`. Par exemple, pour exécuter la cible `Clean`, puis la cible `Compile`, tapez :  
  
     `<Project DefaultTargets="Clean;Compile">`  
  
## <a name="using-the-target-switch"></a>Utilisation du commutateur /target  
 Si aucune cible par défaut n’est définie dans le fichier projet ou si vous ne voulez pas utiliser cette cible par défaut, vous pouvez utiliser le commutateur de ligne de commande **/target** pour spécifier une autre cible. La ou les cibles spécifiées avec le commutateur **/target** sont exécutées à la place des cibles spécifiées par l’attribut `DefaultTargets`. Les cibles spécifiées dans l’attribut `InitialTargets` sont toujours exécutées en premier.  
  
#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Pour utiliser en premier une cible autre que la cible par défaut  
  
-   Spécifiez la cible comme première cible à l’aide du commutateur de ligne de commande **/target**. Exemple :  
  
     `msbuild file.proj /target:Clean`  
  
#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Pour utiliser en premier plusieurs cibles autres que les cibles par défaut  
  
-   Répertoriez les cibles, séparées par des points-virgules ou des virgules, à l’aide du commutateur de ligne de commande **/target**. Exemple :  
  
     `msbuild <file name>.proj /t:Clean;Compile`  
  
## <a name="see-also"></a>Voir aussi
  [MSBuild](../msbuild/msbuild.md)  
 [Targets (Cibles MSBuild)](../msbuild/msbuild-targets.md)   
 [Guide pratique pour nettoyer une build](../msbuild/how-to-clean-a-build.md)