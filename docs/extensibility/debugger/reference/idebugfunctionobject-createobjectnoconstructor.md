---
title: IDebugFunctionObject::CreateObjectNoConstructor | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords: IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 52ba30532cb1a673b61e44874e3938ca1ee3ad06
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfunctionobjectcreateobjectnoconstructor"></a>IDebugFunctionObject::CreateObjectNoConstructor
Crée un objet avec aucun constructeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateObjectNoConstructor(   
   IDebugField*   pClassObject,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateObjectNoConstructor(  
   IDebugField      pClassField,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pClassObject`  
 [in] Un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet représentant le type de l’objet à créer.  
  
 `ppObject`  
 [out] Retourne un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant l’objet qui vient d’être créé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Appelez cette méthode pour créer un objet qui représente une instance d’une structure ou un type complexe (qui ne nécessite pas un constructeur) qui est un paramètre à la fonction qui est représentée par le [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface.  
  
 Si le paramètre d’objet requiert un constructeur, appelez le [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)