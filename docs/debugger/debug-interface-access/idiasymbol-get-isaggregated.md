---
title: IDiaSymbol::get_isAggregated | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_isAggregated method
ms.assetid: 24d280ef-6ea3-4958-9418-4ad3ca7c67c1
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0da925fa76eb477a5995815f74a664899e721640
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetisaggregated"></a>IDiaSymbol::get_isAggregated
Récupère un indicateur qui spécifie si le symbole de données fait partie d’un agrégat ou une collection de symboles ; le compilateur traite les symboles agrégées comme des entités distinctes, mais elles sont réellement partie d’un seul symbole supérieure.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_isAggregated(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pFlag`  
 [out] Retourne `TRUE` si les données font partie d’une agrégation de symboles fractionnés d’un symbole parent ; sinon, retourne `FALSE`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Remarques  
 Le [IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md) méthode est `TRUE` pour le symbole qui est le parent des symboles agrégées.  
  
## <a name="requirements"></a>Spécifications  
  
|Spécification|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK 8.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)