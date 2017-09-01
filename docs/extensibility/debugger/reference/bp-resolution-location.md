---
title: BP_RESOLUTION_LOCATION | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
caps.latest.revision: 10
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
ms.openlocfilehash: 82945a764887f47e11d7878417e96f77b9dba1a2
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="bpresolutionlocation"></a>BP_RESOLUTION_LOCATION
Specifies the structure of the breakpoint resolution location.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
struct _BP_RESOLUTION_LOCATION {  
   BP_TYPE bpType;  
   union {  
      BP_RESOLUTION_CODE bpresCode;  
      BP_RESOLUTION_DATA bpresData;  
      int                unused;  
   } bpResLocation;  
} BP_RESOLUTION_LOCATION;  
```  
  
```csharp  
public struct BP_RESOLUTION_LOCATION {  
   public uint bpType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public uint   unionmember4;  
};  
```  
  
## <a name="members"></a>Members  
 `bpType`  
 A value from the [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) enumeration that specifies how to interpret the `bpResLocation` union or `unionmemberX` members.  
  
 `bpResLocation.bpresCode`  
 [C++ only] Contains the [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) structure if `bpType` = `BPT_CODE`.  
  
 `bpResLocation.bpresData`  
 [C++ only] Contains the [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) structure if `bpType` = `BPT_DATA`.  
  
 `bpResLocation.unused`  
 [C++ only] A placeholder.  
  
 `unionmember1`  
 [C# only] See Remarks on how to interpret.  
  
 `unionmember2`  
 [C# only] See Remarks on how to interpret.  
  
 `unionmember3`  
 [C# only] See Remarks on how to interpret.  
  
 `unionmember4`  
 [C# only] See Remarks on how to interpret.  
  
## <a name="remarks"></a>Remarks  
 This structure is a member of the [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) and [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) structures.  
  
 [C# only] The `unionmemberX` members are interpreted according to the following table. Look down the left column for the `bpType` value then across to determine what each `unionmemberX` member represents and marshal the `unionmemberX` accordingly. See the Example for a way to interpret this structure in C#.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|  
|`BPT_DATA`|`string` (data expression)|`string` (function name)|`string` (image name)|`enum_BP_RES_DATA_FLAGS`|  
  
## <a name="example"></a>Example  
 This example shows how to interpret the `BP_RESOLUTION_LOCATION` structure in C#.  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(BP_RESOLUTION_LOCATION bprl)  
        {  
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)  
            {  
                 IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);  
            }  
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)  
            {  
                 string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);  
                 string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Requirements  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>See Also  
 [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)