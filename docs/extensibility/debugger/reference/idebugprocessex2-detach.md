---
title: IDebugProcessEx2::Detach | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
caps.latest.revision: 15
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
ms.openlocfilehash: d3ba5d8ea92200a70623a6e53ceb484aadfc3af2
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
This method informs the process that a session is no longer debugging the process.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Detach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Detach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pSession`  
 [in] A value that uniquely identifies the session to detach this process from.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 The interface passed in `pSession` is to be treated only as a cookie, a value that uniquely identifies the session debug manager that originally attached to this process; none of the methods on the supplied interface are functional.  
  
## <a name="see-also"></a>See Also  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)