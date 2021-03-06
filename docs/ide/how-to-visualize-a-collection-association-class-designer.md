---
title: Guide pratique pour visualiser une association de collections (Concepteur de classes) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 53eb6ed7e8025ee6cc9a9a3ee8161078accbc457
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-visualize-a-collection-association-class-designer"></a>Comment : visualiser une association de collections (Concepteur de classes)
Les propriétés et les champs qui sont des collections d’autres types peuvent être affichés sur le diagramme de classes en tant qu’association de collection. Contrairement à une association normale, qui affiche un champ ou une propriété sous la forme d’une ligne reliant la classe propriétaire au type du champ, une association de collection s’affiche sous la forme d’une ligne reliant la classe propriétaire au type collecté.  
  
### <a name="to-create-a-collection-association"></a>Pour créer une association de collection  
  
1.  Dans le code, créez une propriété ou un champ dont le type est lui-même une collection fortement typée.  
  
2.  Dans le diagramme de classes, développez la classe afin que les champs et propriétés soient affichés.  
  
3.  Dans la classe, cliquez avec le bouton droit sur le champ ou la propriété, puis choisissez **Afficher en tant qu’association de collection**.  
  
     La propriété ou le champ s’affiche sous la forme d’une ligne reliée au type collecté.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour créer des associations entre les types (Concepteur de classes)](../ide/how-to-create-associations-between-types-class-designer.md)   
 [Conception des classes et des types (Concepteur de classes)](../ide/designing-classes-and-types-class-designer.md)   
 [Affichage des types et relations (Concepteur de classes)](../ide/viewing-types-and-relationships-class-designer.md)