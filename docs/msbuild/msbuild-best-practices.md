---
title: "Bonnes pratiques pour MSBuild | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 881075ee32ccac155237035dbe1a2f6d17a82893
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-best-practices"></a>Meilleures pratiques pour MSBuild
Nous vous recommandons les meilleures pratiques suivantes pour l'écriture de scripts MSBuild :  
  
-   Les valeurs de propriété par défaut sont mieux gérées en utilisant l'attribut `Condition` plutôt qu'en déclarant une propriété dont la valeur par défaut peut être substituée sur la ligne de commande. Par exemple, utilisez  
  
     `<MyProperty Condition="'$(MyProperty)' == ''">`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   Évitez les caractères génériques quand vous sélectionnez des éléments. Spécifiez plutôt les fichiers de manière explicite. Les erreurs susceptibles de se produire quand vous ajoutez ou supprimez des fichiers sont ainsi plus faciles à localiser.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts avancés](../msbuild/msbuild-advanced-concepts.md)
