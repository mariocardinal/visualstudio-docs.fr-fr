---
title: CONTEXT_INFO | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
caps.latest.revision: 11
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 9d2ecfdd70c2c299704b89de1cacec321f0ecdc1
ms.lasthandoff: 02/22/2017

---
# <a name="contextinfo"></a>CONTEXT_INFO
Un contexte de la mémoire ou code décrite par cette structure.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
typedef struct _tagCONTEXT_INFO {   
   CONTEXT_INFO_FIELDS dwFields;  
   BSTR                bstrModuleUrl;  
   BSTR                bstrFunction;  
   TEXT_POSITION       posFunctionOffset;  
   BSTR                bstrAddress;  
   BSTR                bstrAddressOffset;  
   BSTR                bstrAddressAbsolute;  
} CONTEXT_INFO;  
```  
  
```c#  
public struct CONTEXT_INFO {  
   public uint          dwFields;  
   public string        bstrModuleUrl;  
   public string        bstrFunction;  
   public TEXT_POSITION posFunctionOffset;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrAddressAbsolute;  
};  
```  
  
## <a name="members"></a>Membres  
 dwFields  
 Une combinaison d’indicateurs d’il [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) énumération qui spécifie les champs sont remplis**.**  
  
 bstrModuleUrl  
 Le nom du module où se trouve le contexte.  
  
 bstrFunction  
 Le nom de la fonction où se trouve le contexte.  
  
 posFunctionOffset  
 A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) structure qui identifie l’offset de colonne et de ligne de la fonction associée au contexte du code.  
  
 bstrAddress  
 L’adresse dans le code où se trouve le contexte donné.  
  
 bstrAddressOffset  
 Le décalage de l’adresse dans le code où se trouve le contexte donné.  
  
 bstrAddressAbsolute  
 L’adresse absolue en mémoire où se trouve le contexte donné.  
  
## <a name="remarks"></a>Remarques  
 Cette structure est retournée à partir d’un appel à la [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) méthode.  
  
 Une utilisation typique de cette structure est à l’appui d’un **mémoire** fenêtre de débogage.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)