---
title: IDebugProperty2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2
helpviewer_keywords: IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 45ad3a6c0d250136d0ab3e1becb088ea140b42e8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty2"></a>IDebugProperty2
Cette interface représente une propriété de frame de pile, une propriété de document du programme ou une autre propriété. La propriété est généralement le résultat d’une évaluation d’expression.  
  
> [!NOTE]
>  Cette utilisation de « propriété » ne doit pas être confondue avec cette variable de membre d’une classe, ce qui signifie que même si un `IDebugProperty2` peut représenter une telle entité.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le D’implémente cette interface pour représenter une valeur particulière. Par exemple, la valeur peut être une valeur numérique à la suite d’une évaluation d’expression, un contexte de la mémoire utilisée pour l’affichage de mémoire ou une liste des registres et leurs valeurs.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Appelez [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour obtenir cette interface, qui représente le résultat d’une évaluation. `IDebugExpression2::EvaluateAsync`Retourne cette interface en envoyant un [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interface pour le SDM, qui à son tour appelle [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) pour récupérer la propriété.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) renvoie cette interface pour fournir le document de script associé.  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) renvoie cette interface pour représenter la valeur de retour d’une fonction.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) renvoie cette interface pour représenter les différentes propriétés du programme comme un nom ou un contexte de la mémoire.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) renvoie cette interface pour représenter les différentes propriétés du frame de pile tels que des variables locales.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugProperty2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Remplit un [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) structure qui décrit une propriété.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Définit la valeur d’une propriété à partir d’une chaîne.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Définit la valeur de la propriété de la valeur de la référence donnée.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Énumère les enfants d’une propriété.|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Retourne le parent d’une propriété.|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Retourne la propriété qui décrit la propriété la plus dérivée d’une propriété.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Retourne les octets de mémoire qui composent la valeur d’une propriété.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Retourne le contexte de la mémoire pour une valeur de propriété.|  
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Retourne la taille, en octets, de la valeur de propriété.|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Retourne une référence à la valeur de cette propriété.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Retourne les informations étendues d’une propriété.|  
  
## <a name="remarks"></a>Remarques  
 Une propriété, telle que représentée par un `IDebugProperty2` l’interface, peut être considéré comme une valeur avec un nom, un type et une adresse. En termes plus générales, un `IDebugProperty2` peut représenter tout ce qui a une structure hiérarchique, avec parents et nœuds enfants.  
  
 Une propriété est généralement transitoire, dure aussi longtemps que le frame de pile actuel, par exemple. En revanche, une référence, comme représenté par un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) interface dure tant que la valeur reste en mémoire.  
  
 L’IDE peut utiliser le `IDebugProperty2` interface pour permettre aux utilisateurs de parcourir et modifier les propriétés au moment de l’exécution.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)