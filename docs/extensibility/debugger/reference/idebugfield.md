---
title: IDebugField | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 1e978ece2ecf56735dc538324b5c148f7f85b9bb
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="idebugfield"></a>IDebugField
This interface represents a field, that is, a description of a symbol or type.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes for Implementers  
 A symbol provider implements this interface as the base class for all fields.  
  
## <a name="notes-for-callers"></a>Notes for Callers  
 This interface is the base class for all fields. Based on the return value of [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), this interface may return more specialized interfaces by using [QueryInterface](/cpp/atl/queryinterface). In addition, many interfaces return `IDebugField` objects from various methods.  
  
## <a name="methods-in-vtable-order"></a>Methods in Vtable Order  
 The following table shows the methods of `IDebugField`.  
  
|Method|Description|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Gets displayable information about the symbol or type.|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Gets the kind of field.|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Gets the type of field.|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Gets the container of the field.|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Gets the address of the field.|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Gets the size of a field, in bytes.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Gets extended information about a field.|  
|[Equal](../../../extensibility/debugger/reference/idebugfield-equal.md)|Compares two fields.|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Gets type-independent information about the symbol or type.|  
  
## <a name="remarks"></a>Remarks  
 A type is equivalent to a C language `typedef`.  
  
 In the following C++ language example, `weather` is a class type, and `sunny` and `stormy` are symbols:  
  
```cpp  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 Whether a field represents a symbol or type can be determined by calling [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) and examining the [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) result. If the `FIELD_KIND_TYPE` bit is set, the field is a type, and if the `FIELD_KIND_SYMBOL` bit is set, it is a symbol.  
  
## <a name="requirements"></a>Requirements  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>See Also  
 [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)