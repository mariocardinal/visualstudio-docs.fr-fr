---
title: "Boîte de dialogue de l’éditeur de conditions de règle (héritée) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords: Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 98a42547786e15815ef760e9f397c3c469c4a1a1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Éditeur de conditions de règle, boîte de dialogue (héritée)
Cette rubrique décrit comment utiliser le **éditeur de conditions de règle** boîte de dialogue de l’héritage [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]. Utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Vous créez et modifiez des conditions de règle déclarative à l’aide de la **éditeur de conditions de règle** boîte de dialogue. Ces conditions de règle sont exposées comme propriétés pour les activités prédéfinies Windows Workflow Foundation suivantes :  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [Activité WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
 Vous accédez à la **éditeur de conditions de règle** boîte de dialogue à l’aide de la [sélectionner une boîte de dialogue Condition (hérité)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
 Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **éditeur de conditions de règle** boîte de dialogue.  
  
|Élément d'interface utilisateur|Description|  
|----------------|-----------------|  
|**Condition :**|Entrez l'expression applicable à la condition de règle.|  
|**BIEN**|Cliquez pour enregistrer la condition de règle.|  
  
## <a name="entering-condition-expressions"></a>Entrée d'expressions de condition  
 Les expressions de condition sont entrées sous forme de texte. Vous pouvez taper **cela.** dans l’éditeur pour référencer des champs, propriétés et méthodes utilisées dans le flux de travail, à l’aide d’un-de menu IntelliSense. Vous pouvez également taper directement un nom de membre de workflow. Vous pouvez ajouter des opérateurs logiques à la condition, tels que les opérateurs AND, OR ou NOT. Vous pouvez également ajouter des prédicats. Un prédicat se compose d’un opérateur binaire et de deux opérandes. Les opérateurs binaires pris en charge sont  **==** ,  **>** ,  **\<** ,  **>=** , et  **<=** . Les opérandes pris en charge sont à valeur de constante, à fonction arithmétique et à portée publique.  
  
 Vous pouvez spécifier le type de comparaison, et vous pouvez comparer aux **null** ou une chaîne vide. Vous pouvez imbriquer des appels à des membres sur une variable qui contient un type complexe, par exemple `this.Address.State == "WA"`.  
  
 L'éditeur de conditions de règle prend en charge les opérateurs suivants :  
  
-   Opérateurs relationnels: ==, =, !=  
  
-   Opérateurs de comparaison : <, \<=, >, > =  
  
-   Opérateurs arithmétiques: +, - , *, /, MOD  
  
-   Opérateurs logiques : et, & &, OR, &#124; &#124; NOT, !  
  
-   Opérateurs au niveau du bit : &, &#124;  
  
 La priorité des opérateurs d'expression suit les règles de priorité des opérateurs C#.  
  
 L'éditeur de conditions de règle prend en charge les opérateurs numériques suivants :  
  
 this.i == 1D (la résolution est 1.0)  
  
 this.i == 1E1 (la résolution est 10.0)  
  
 this.i == 1L (la résolution est un entier long)  
  
 this.i == 1M (la résolution est un nombre décimal)  
  
 this.i == 1F (la résolution est un nombre unique)  
  
 this.i == 1U (la résolution est un unsigned int)  
  
 Pour plus d’informations sur les conditions, consultez [à l’aide de Conditions dans les Workflows](http://go.microsoft.com/fwlink?LinkID=65009).  
  
## <a name="see-also"></a>Voir aussi  
 [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)   
 [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)   
 [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)   
 [Activité WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)   
 [Sélectionnez la Condition, boîte de dialogue (héritée)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [À l’aide de Conditions dans les Workflows](http://go.microsoft.com/fwlink?LinkID=65009)   
 [Aide de l’interface utilisateur du concepteur hérité pour Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)