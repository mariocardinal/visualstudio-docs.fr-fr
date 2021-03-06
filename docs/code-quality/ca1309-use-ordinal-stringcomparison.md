---
title: "CA1309 : Utiliser StringComparison avec la valeur ordinale | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ba777ea4cd272a1392413a2ecbb52b9f45a3d71b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309 : Utiliser StringComparison avec la valeur Ordinal
|||  
|-|-|  
|TypeName|UseOrdinalStringComparison|  
|CheckId|CA1309|  
|Catégorie|Microsoft.Globalization|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Une opération de comparaison de chaînes non linguistique qui ne pas défini la <xref:System.StringComparison> paramètre soit **Ordinal** ou **OrdinalIgnoreCase**.  
  
## <a name="rule-description"></a>Description de la règle  
 Plusieurs opérations de chaîne, la plus importantes du <xref:System.String.Compare%2A?displayProperty=fullName> et <xref:System.String.Equals%2A?displayProperty=fullName> méthodes fournissent désormais une surcharge qui accepte un <xref:System.StringComparison?displayProperty=fullName> valeur d’énumération en tant que paramètre.  
  
 Lorsque vous définissez **StringComparison.Ordinal** ou **StringComparison.OrdinalIgnoreCase**, la comparaison de chaînes est non linguistique. Autrement dit, les fonctionnalités qui sont spécifiques au langage naturel sont ignorées lors de décisions de comparaison. Cela signifie que les décisions reposent sur simples comparaisons d’octets et ignorer la casse ou équivalence des tables qui sont paramétrables par la culture. Par conséquent, en affectant explicitement le paramètre soit le **StringComparison.Ordinal** ou **StringComparison.OrdinalIgnoreCase**, votre code souvent accélère augmente l’exactitude et devient plus fiable.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, modifiez la méthode de comparaison de chaînes une surcharge qui accepte le <xref:System.StringComparison?displayProperty=fullName> énumération en tant que paramètre et spécifier **Ordinal** ou **OrdinalIgnoreCase**. Par exemple, remplacez `String.Compare(str1, str2)` à `String.Compare(str1, str2, StringComparison.Ordinal)`.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle lorsque la bibliothèque ou l’application est destiné à une audience locale limitée ou lorsque la sémantique de la culture actuelle doit être utilisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Avertissements de globalisation](../code-quality/globalization-warnings.md)   
 [CA1307 : Spécifiez StringComparison](../code-quality/ca1307-specify-stringcomparison.md)