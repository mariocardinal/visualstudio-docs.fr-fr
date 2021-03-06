---
title: "CA2122 : N’exposez pas indirectement des méthodes avec des demandes de liaison | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 00222c71e537856d420c6472efb104a8c928237e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122 : N'exposez pas indirectement des méthodes avec des demandes de liaison
|||  
|-|-|  
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|  
|CheckId|CA2122|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un membre public ou protégé a un [les demandes de liaison](/dotnet/framework/misc/link-demands) et est appelé par un membre qui n’effectue pas de vérifications de sécurité.  
  
## <a name="rule-description"></a>Description de la règle  
 Une demande de liaison vérifie uniquement les autorisations de l'appelant immédiat. Si un membre `X` n’effectue des demandes de sécurité aucun de ses appelants et appelle un code protégé par une demande de liaison, un appelant sans l’autorisation nécessaire peut utiliser `X` pour accéder au membre protégé.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Ajouter une sécurité [données et modélisation](/dotnet/framework/data/index) ou demande de liaison au membre afin qu’il ne fournit plus accès non sécurisé au membre protégé par demande de liaison.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Pour supprimer sans risque un avertissement de cette règle, il se peut que vous devez vous assurer que votre code n’accorde pas ses appelants accès à des opérations ou des ressources qui peuvent être utilisées dans une action destructrice.  
  
## <a name="example"></a>Exemple  
 Les exemples suivants montrent une bibliothèque qui enfreint la règle et une application qui montre la faiblesse de la bibliothèque. L’exemple de bibliothèque fournit deux méthodes qui ensemble enfreint la règle. Le `EnvironmentSetting` (méthode) est sécurisée par une demande de liaison pour un accès illimité aux variables d’environnement. Le `DomainInformation` méthode n’effectue aucune des demandes de sécurité de ses appelants avant d’appeler `EnvironmentSetting`.  
  
 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]  
  
## <a name="example"></a>Exemple  
 L’application suivante appelle le membre de bibliothèque non sécurisé.  
  
 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]  
  
 Cet exemple produit la sortie suivante.  
  
 **Valeur de membre : seattle.corp.contoso.com**   
## <a name="see-also"></a>Voir aussi  
 [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines)   
 [Demandes de liaison](/dotnet/framework/misc/link-demands)   
 [Données et modélisation](/dotnet/framework/data/index)