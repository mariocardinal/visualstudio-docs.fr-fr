---
title: Refactorisation des classes et des types (Concepteur de classes) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.ClassDesigner.OverrideMembersDialog
helpviewer_keywords:
- members, overriding
- overriding members
- classes [Visual Studio], refactoring
- type members, overriding
- refactoring, types
- types [Visual Studio], refactoring
- Class Designer [Visual Studio], refactoring classes
- refactoring, classes
ms.assetid: dcf07bb4-fa3b-4224-9dec-566fd924a8ce
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b18680e10adbd3bd1e91c821f1d1e9381dd96759
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="refactoring-classes-and-types-class-designer"></a>Refactorisation des classes et des types (Concepteur de classes)
Quand vous refactorisez du code, vous le rendez plus facile à comprendre et à gérer. Vous le rendez également plus efficace en changeant sa structure interne et la conception de ses objets, sans altérer son comportement externe. Utilisez le Concepteur de classes et la fenêtre Détails de classe pour réduire votre charge de travail et limiter le risque d'introduire des bugs quand vous refactorisez du code Visual C# .NET, Visual Basic .NET ou C++ dans votre projet Visual Studio.  
  
> [!NOTE]
>  Les fichiers d'un projet peuvent être en lecture seule, car le projet est sous contrôle de code source et n'est pas extrait (projet référencé), ou ses fichiers sont marqués en lecture seule sur le disque. Quand vous travaillez dans un projet ayant l’un de ces états, vous avez plusieurs façons différentes d’enregistrer votre travail. Cela s'applique au code que vous refactorisez et au code que vous changez d'une autre façon, par exemple en le modifiant directement. Pour plus d’informations, consultez [Affichage d’informations en lecture seule (Concepteur de classes)](http://msdn.microsoft.com/en-us/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).  
  
## <a name="common-tasks"></a>Tâches courantes  
  
|Tâche|Contenu de support|  
|----------|------------------------|  
|**Refactorisation des classes** : vous pouvez utiliser les opérations de refactorisation pour fractionner une classe en classes partielles ou pour implémenter une classe de base abstraite.|-   [Guide pratique pour fractionner une classe en classes partielles (Concepteur de classes)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md)|  
|**Utilisation des interfaces** : dans le Concepteur de classes, vous pouvez implémenter une interface pour le diagramme de classes en la connectant à une classe qui fournit du code pour les méthodes d’interface.|-   [Guide pratique pour implémenter une interface (Concepteur de classes)](../ide/how-to-implement-an-interface-class-designer.md)|  
|**Refactorisation des types, des membres de type et des paramètres** : à l’aide du Concepteur de classes, vous pouvez renommer des types, substituer des membres de type ou les déplacer d’un type à un autre. Vous pouvez également créer des types Nullable.|-   [Attribution d'un nouveau nom aux types et membres de type](../ide/refactoring-classes-and-types-class-designer.md#RenamingTypesAndMembers)<br />-   [Déplacement des membres de type d’un type à un autre](../ide/refactoring-classes-and-types-class-designer.md#MovingTypeMembers)<br />-   [Guide pratique pour créer un type Nullable (Concepteur de classes)](../ide/how-to-create-a-nullable-type-class-designer.md)|  
  
###  <a name="RenamingTypesAndMembers"></a> Attribution d’un nouveau nom aux types et membres de type  
 Au sein du Concepteur de classes, vous pouvez renommer un type ou un membre de type dans le diagramme de classes ou dans la fenêtre Propriétés. Dans la fenêtre Détails de classe, vous pouvez changer le nom d'un membre mais pas d'un type. Le changement de nom d'un type ou d'un membre de type se propage à toutes les fenêtres et tous les emplacements de code où apparaissait l'ancien nom.  
  
##### <a name="to-rename-a-name-in-the-class-designer"></a>Pour attribuer un nouveau nom dans le Concepteur de classes  
  
1.  Dans le diagramme de classes, sélectionnez le type ou le membre, puis cliquez sur le nom.  
  
     Le nom du membre devient modifiable.  
  
2.  Tapez le nouveau nom du membre de type ou du type  
  
##### <a name="to-rename-a-name-in-the-class-details-window"></a>Pour attribuer un nouveau nom dans la fenêtre Détails de classe  
  
1.  Pour afficher la fenêtre Détails de classe, cliquez avec le bouton droit sur le type ou le membre de type, puis cliquez sur **Détails de classe**.  
  
     La fenêtre Détails de classe s'affiche.  
  
2.  Dans la colonne **Nom** , changez le nom du membre de type.  
  
3.  Pour déplacer le focus hors de la cellule, appuyez sur la touche **Entrée** ou cliquez en dehors de la cellule.  
  
    > [!NOTE]
    >  Dans la fenêtre Détails de classe, vous pouvez changer le nom d'un membre mais pas d'un type.  
  
##### <a name="to-rename-a-name-in-the-properties-window"></a>Pour attribuer un nouveau nom dans la fenêtre Propriétés  
  
1.  Dans le diagramme de classes ou la fenêtre Détails de classe, cliquez avec le bouton droit sur le type ou le membre, puis cliquez sur **Propriétés**.  
  
     La fenêtre Propriétés apparaît et affiche les propriétés du type ou du membre de type.  
  
2.  Dans la propriété **Nom** , changez le nom du type ou du membre de type.  
  
     Le nouveau nom se propage à l'ensemble des fenêtres et des emplacements de code du projet actif, où apparaissait l'ancien nom.  
  
###  <a name="MovingTypeMembers"></a> Déplacement des membres de type d'un type à un autre  
 À l'aide du **Concepteur de classes**, vous pouvez déplacer un membre de type d'un type à un autre, si les deux types sont visibles dans le diagramme de classes actif.  
  
##### <a name="to-move-a-type-member-from-one-type-to-another"></a>Pour déplacer un membre de type d'un type à un autre  
  
1.  Dans un type visible sur l'aire de conception, cliquez avec le bouton droit sur le membre à déplacer vers un autre type, puis cliquez sur **Couper**.  
  
2.  Cliquez avec le bouton droit sur le type de destination, puis cliquez sur **Coller**.  
  
     La propriété est supprimée du type source et apparaît dans le type de destination.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Affichage des types et relations (Concepteur de classes)](../ide/viewing-types-and-relationships-class-designer.md)||  
|[Conception des classes et des types (Concepteur de classes)](../ide/designing-classes-and-types-class-designer.md)||