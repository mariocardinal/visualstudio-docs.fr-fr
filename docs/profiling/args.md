---
title: Args | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87c483cea9b174e330cd951d55eb287807d8262a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="args"></a>Args
L’option **Args** de VSPerfCmd.exe spécifie la liste des arguments qui sont passés à l’application cible de la sous-commande **Launch**.  
  
 **Args** ne peut être utilisé que si **Launch** est également spécifié sur la ligne de commande. **Args** est facultatif lorsque **Launch** est spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Arguments`  
 Liste d’arguments de l’application cible de la commande **Launch**.  
  
## <a name="required-options"></a>Options obligatoires  
 **Launch:** `AppName`  
 Démarre l’application spécifiée et commence le profilage avec la méthode d’échantillonnage.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’option **Args** pour passer des arguments à TestApp.exe.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)