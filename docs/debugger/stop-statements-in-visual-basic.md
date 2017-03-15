---
title: "Instructions Stop en Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
helpviewer_keywords: 
  - "points d'arrêt, instructions Stop"
  - "déboguer (Visual Basic), instruction Stop et points d'arrêt"
  - "déboguer le code managé, instruction Stop et points d'arrêt"
  - "instructions End"
  - "instructions Stop, à propos des instructions Stop"
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Instructions Stop en Visual Basic
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'instruction Stop de Visual Basic fournit une alternative de programmation à la définition d'un point d'arrêt.  Lorsque le débogueur rencontre une instruction Stop, il interrompt l'exécution du programme \(passe en mode arrêt\).  Les programmeurs C\# peuvent parvenir au même résultat à l'aide d'un appel à System.Diagnostics.Debugger.Break.  
  
 Vous définissez ou supprimez une instruction Stop en modifiant votre code source.  Vous ne pouvez pas définir ou supprimer des instructions Stop en utilisant des commandes du débogueur, comme pour un point d'arrêt.  
  
 À la différence d'une instruction End, l'instruction Stop ne réinitialise pas les variables ou ne retourne pas en mode design.  Vous pouvez choisir Continuer dans le menu Déboguer pour poursuivre l'exécution de l'application.  
  
 Lorsque vous exécutez une application Visual Basic en dehors du débogueur, une instruction Stop lance le débogueur si le débogage juste\-à\-temps est activé.  Si le débogage juste\-à\-temps n'est pas activé, l'instruction Stop se comporte comme si une instruction End était présente, et l'exécution prend fin.  Si aucun événement QueryUnload ou Unload ne se produit, vous devez supprimer toutes les instructions Stop de la version Release de votre application Visual Basic.  Pour plus d'informations, consultez [Débogage juste\-à\-temps](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Pour éviter de supprimer les instructions Stop, vous pouvez utiliser la compilation conditionnelle :  
  
```  
#If DEBUG Then  
   Stop  
#Else  
   ' Don't stop  
#End If  
```  
  
 Vous pouvez également utiliser une instruction Assert à la place de l'instruction Stop.  Une instruction Debug.Assert interrompt l'exécution uniquement lorsqu'une condition spécifique n'est pas vérifiée et est automatiquement supprimée lorsque vous compilez une version Release.  Pour plus d'informations, consultez [Assertions dans du code managé](../debugger/assertions-in-managed-code.md).  Si vous souhaitez utiliser une instruction Assert qui interrompt toujours l'exécution en version Debug, procédez comme suit :  
  
```  
Debug.Assert(false)  
```  
  
 Vous pouvez également utiliser la méthode Debug.Fail :  
  
```  
Debug.Fail("a clever output string goes here")  
```  
  
## Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Types de projets C\#, F\# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Débogage du code managé](../debugger/debugging-managed-code.md)