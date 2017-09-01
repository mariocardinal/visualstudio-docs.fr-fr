---
title: IDebugOutputStringEvent2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 42a3b630a501a379d38a53f942c0aceb494d94d7
ms.lasthandoff: 04/05/2017

---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
Cette interface est envoyée par le moteur de débogage (DE) pour le Gestionnaire de session de débogage (SDM) à une chaîne de sortie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugOutputStringEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le D’implémente cette interface pour envoyer une chaîne à la **sortie** fenêtre de l’IDE. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à la `IDebugEvent2` interface.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Le crée et envoie cet objet d’événement pour envoyer une chaîne à la **sortie** fenêtre. L’événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente la méthode de `IDebugOutputStringEvent2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Obtient le message peut être affichée.|  
  
## <a name="remarks"></a>Remarques  
 Par exemple, dans le code non managé, la chaîne de sortie peut provenir de lorsque le programme débogué envoie une chaîne vers Win32 `OutputDebugString` (fonction). Cette chaîne est interceptée par le DE et envoyée à le SDM comme le `IDebugOutputStringEvent2` événement.  
  
 Utilisez [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) pour envoyer un message qui requiert une réponse de l’utilisateur.  
  
 Utilisez [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) pour envoyer un message d’erreur qui ne nécessite pas de réponse.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)