---
title: DEBUG_CUSTOM_VIEWER | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DEBUG_CUSTOM_VIEWER
helpviewer_keywords: DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cc6f9655d2ec7bc588bcd673d5331f12f7fab262
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="debugcustomviewer"></a>DEBUG_CUSTOM_VIEWER
Une structure qui identifie une visionneuse personnalisée ou le type de visualiseur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct tagDEBUG_CUSTOM_VIEWER {  
   DWORD dwID;  
   BSTR  bstrMenuName;  
   BSTR  bstrDescription;  
   GUID  guidLang;  
   GUID  guidVendor;  
   BSTR  bstrMetric;  
} DEBUG_CUSTOM_VIEWER;  
```  
  
```csharp  
public struct DEBUG_CUSTOM_VIEWER {  
   public uint   dwID;  
   public string bstrMenuName;  
   public string bstrDescription;  
   public Guid   guidLang;  
   public Guid   guidVendor;  
   public string bstrMetric;  
};  
```  
  
## <a name="members"></a>Membres  
 dwID  
 Un ID pour différencier plusieurs visionneuses ou implémentées par un visualiseurs `GUID`.  
  
 bstrMenuName  
 Le texte qui apparaît dans le menu déroulant.  
  
 bstrDescription  
 Description de la visionneuse personnalisée ou d’un visualiseur de type (doit être une valeur null si non utilisé).  
  
 guidLang  
 Langue de l’évaluateur d’expression en fournissant.  
  
 guidVendor  
 Fournisseur de l’évaluateur d’expression en fournissant.  
  
 bstrMetric  
 Métrique sous lequel la visionneuse personnalisée ou un visualiseur de type `CLSID` est stocké.  
  
## <a name="remarks"></a>Remarques  
 Une liste de cette structure est retournée par un appel à la [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) (méthode) (et, par extension, le [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)