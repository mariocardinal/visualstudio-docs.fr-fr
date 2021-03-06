---
title: "Avertissements de fiabilité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d3ac06911009a24640031fd3a2306110f289014f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="reliability-warnings"></a>avertissements liés à la fiabilité
Avertissements de fiabilité prennent en charge la fiabilité de bibliothèques et des applications, notamment l’utilisation de mémoire et le thread correcte.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Règle|Description|  
|----------|-----------------|  
|[CA2000 : Supprimez les objets avant de perdre l’étendue](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|Sachant qu'un événement exceptionnel peut se produire et empêcher l'exécution du finaliseur d'un objet, ce dernier doit plutôt être supprimé explicitement avant que toutes les références à lui soient hors de portée.|  
|[CA2001 : Évitez d’appeler des méthodes susceptibles de poser des problèmes](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Un membre appelle une méthode potentiellement dangereuse ou problématique.|  
|[CA2002 : Ne définissez pas un verrou sur des objets à identité faible](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Un objet est dit d'identité faible lorsqu'il est accessible directement au-delà des limites d'un domaine d'application. Un thread qui essaie d'acquérir un verrou sur un objet qui affiche une identité faible peut être bloqué par un deuxième thread dans un domaine d'application différent qui dispose d'un verrou sur le même objet.|  
|[CA2003 : Ne traitez pas les fibres comme des threads](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Un thread managé est traité comme un thread Win32.|  
|[CA2004 : Supprimez les appels à GC.KeepAlive](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Si vous convertissez d’utiliser SafeHandle, supprimez tous les appels à GC. KeepAlive (objet). Dans ce cas, les classes ne devez pas appeler GC. KeepAlive, en supposant qu’ils n’ont pas de finaliseur, mais dépendent de SafeHandle pour finaliser le système d’exploitation gérer pour eux.|  
|[CA2006 : Utilisez SafeHandle pour encapsuler les ressources natives](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|L'utilisation de IntPtr dans du code managé peut être le signe d'un problème potentiel de sécurité et de fiabilité. Toute utilisation de IntPtr doit être passée en revue pour déterminer s'il est nécessaire de recourir à un SafeHandle ou une technologie similaire à la place.|