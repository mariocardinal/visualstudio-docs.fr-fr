---
title: "Arrêt d’un programme | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ef92896ebdb847dd16e00911dc49b53d9ceb5877
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="terminating-a-program"></a>Arrêt d’un programme
Voici une description de l’arrêt d’un programme avec un thread.  
  
## <a name="termination-process"></a>Processus d’arrêt  
  
1.  L’envoie DE un [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) avec valide [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2.  L’envoie DE un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) avec valide [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
 L’IDE repasse en mode design. Le moteur de débogage ou d’un environnement d’exécution appelle [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) pour supprimer le programme à partir du port.  
  
## <a name="see-also"></a>Voir aussi  
 [Événements d’appel du débogueur](../../extensibility/debugger/calling-debugger-events.md)