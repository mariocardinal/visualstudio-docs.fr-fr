---
title: DEBUG_ADDRESS | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DEBUG_ADDRESS
helpviewer_keywords: DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a112e8b8d2204259fbd3ea003aef957a8c713abf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="debugaddress"></a>DEBUG_ADDRESS
Cette structure représente une adresse.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```csharp  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## <a name="terms"></a>Termes  
 ulAppDomainID  
 L’ID de processus.  
  
 guidModule  
 Le GUID du module qui contient cette adresse.  
  
 tokClass  
 Le jeton d’identification de la classe ou le type de cette adresse.  
  
> [!NOTE]
>  Cette valeur est spécifique à un fournisseur de symbole et par conséquent n’a aucune signification générale, autre que, en tant qu’identificateur pour un type de classe.  
  
 Addr  
 A [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) structure qui contient l’union de structures qui décrivent les types d’adresses individuelles. La valeur `addr`.`dwKind` provient de la [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) énumération, qui explique comment interpréter l’union.  
  
## <a name="remarks"></a>Remarques  
 Cette structure est passée à la [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) (méthode) doit être renseigné.  
  
 **Avertissement (C++ uniquement)**  
  
 Si `addr.dwKind` est `ADDRESS_KIND_METADATA_LOCAL` et si `addr.addr.addrLocal.pLocal` n’est pas une valeur null, vous devez l’appeler `Release` sur le pointeur de jeton :  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)