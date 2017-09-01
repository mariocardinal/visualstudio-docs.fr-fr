---
title: IDebugPortSupplier2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
caps.latest.revision: 13
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 4bc102daaea87a8dff93eb76b0bc42e195fa1f21
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
This interface supplies ports to the session debug manager (SDM).  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes for Implementers  
 A custom port supplier implements this interface to represent a port supplier.  
  
## <a name="notes-for-callers"></a>Notes for Callers  
 A call to `CoCreateInstance` with a port supplier's `GUID` returns this interface (this is the typical way to obtain this interface). For example:  
  
```cpp  
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)  
{  
    IDebugPortSupplier2 *pPS = NULL;  
    if (pPortSupplierGuid != NULL) {  
        CComPtr<IDebugPortSupplier2> spPortSupplier;  
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);  
        if (spPortSupplier != NULL) {  
            pPS = spPortSupplier.Detach();  
        }  
    }  
    return (pPS);  
}  
```  
  
 A call to [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) returns this interface, representing the current port supplier being used by [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  
  
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) returns this interface, representing the port supplier that created the port.  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) represents a list of `IDebugPortSupplier` interfaces (the `IEnumDebugPortSuppliers` interface is obtained from [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), representing all of the port suppliers registered with [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]).  
  
 A debug engine typically does not interact with a port supplier.  
  
## <a name="methods-in-vtable-order"></a>Methods in Vtable Order  
 The following table shows the methods of `IDebugPortSupplier2`.  
  
|Method|Description|  
|------------|-----------------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Gets the port supplier name.|  
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Gets the port supplier identifier.|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Gets a port from a port supplier.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Enumerates the ports that already exist.|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Verifies that a port supplier supports adding new ports.|  
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Adds a port.|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Removes a port.|  
  
## <a name="remarks"></a>Remarks  
 A port supplier can identify itself by name and ID, add and remove ports, and enumerate all ports that the port supplier provides.  
  
## <a name="requirements"></a>Requirements  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>See Also  
 [Core Interfaces](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)