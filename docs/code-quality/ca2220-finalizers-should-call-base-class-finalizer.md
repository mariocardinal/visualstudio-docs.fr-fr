---
title: "CA2220 : Les finaliseurs doivent appeler le finaliseur de la classe de base | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aa5ed3329d4168a0781243a4faf021de3488e77c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220 : Les finaliseurs doivent appeler le finaliseur de leur classe de base
|||  
|-|-|  
|TypeName|FinalizersShouldCallBaseClassFinalizer|  
|CheckId|CA2220|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un type qui substitue <xref:System.Object.Finalize%2A?displayProperty=fullName> n’appelle pas la <xref:System.Object.Finalize%2A> méthode dans sa classe de base.  
  
## <a name="rule-description"></a>Description de la règle  
 La finalisation doit être propagée par le biais de la hiérarchie d'héritage. Pour ce faire, les types doivent appeler leur classe de base <xref:System.Object.Finalize%2A> méthode à partir de leurs propres <xref:System.Object.Finalize%2A> (méthode). Le compilateur c# ajoute automatiquement l’appel au finaliseur de classe de base.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, appelez le type de base <xref:System.Object.Finalize%2A> méthode à partir de votre <xref:System.Object.Finalize%2A> (méthode).  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle. Certains compilateurs qui ciblent le common language runtime insérer un appel au finaliseur du type de base dans le langage intermédiaire Microsoft (MSIL). Si un avertissement de cette règle est signalé, votre compilateur n’insère pas de l’appel, et vous devez l’ajouter à votre code.  
  
## <a name="example"></a>Exemple  
 L’exemple Visual Basic suivant présente un type `TypeB` qui appelle correctement le <xref:System.Object.Finalize%2A> méthode dans sa classe de base.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle de suppression](/dotnet/standard/design-guidelines/dispose-pattern)