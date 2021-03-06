---
title: "Erreur : Vous n’êtes pas autorisé à inspecter le processus &#39; identité de s | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 6233d060-85b8-42be-ae5f-bde7e1d0f241
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e168af69b04fb152e054860b2a6bd2084a349ff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Erreur : Vous n’êtes pas autorisé à inspecter le processus &#39; identité de s
Vous n'êtes pas autorisé à inspecter l'identité du processus. Cela peut être dû à la configuration de votre système.  
  
 Le débogueur n'a pas pu inspecter l'identité du processus, qui contient des informations nécessaires au débogage. La cause la plus probable est la désactivation des services Terminal Server. Les services Terminal Server sont activés par défaut. Pour les réactiver, procédez comme suit.  
  
### <a name="to-enable-terminal-services"></a>Pour activer les services Terminal Server  
  
1.  Cliquez sur **Démarrer** , puis **le panneau de configuration**.  
  
2.  Dans le panneau de configuration, choisissez **basculer vers l’affichage classique**, si nécessaire, puis double-cliquez sur **outils d’administration**.  
  
3.  Dans le **outils d’administration** fenêtre, double-cliquez sur **gestion de l’ordinateur**.  
  
4.  Dans la fenêtre Gestion de l’ordinateur, développez le **Services et Applications** nœud.  
  
5.  Sous le **Services et Applications**, cliquez sur **Services**.  
  
     Une liste de services apparaît dans le volet droit.  
  
6.  Dans le **Services** liste, cliquez sur **Services Terminal Server** , puis **propriétés**.  
  
7.  Dans le **propriétés des Services Terminal Server** fenêtre, accédez à la **général** onglet et définissez **type de démarrage** à **manuel**.  
  
8.  Cliquez sur **OK**.  
  
9. Redémarrez l'ordinateur.  
  
     Cette procédure n'active pas automatiquement le Bureau à distance. Pour activer le Bureau à distance sur votre ordinateur, effectuez la procédure supplémentaire suivante.  
  
### <a name="to-enable-remote-desktop"></a>Pour activer le Bureau à distance  
  
1.  Cliquez sur **Démarrer** , cliquez sur **poste**.  
  
2.  Choisissez **propriétés**.  
  
     Le **propriétés système** fenêtre s’affiche.  
  
3.  Cliquez sur **distant**.  
  
4.  Sous **Bureau à distance**, sélectionnez **permettre aux utilisateurs de se connecter à distance à cet ordinateur**.  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs et résolution des problèmes du débogage distant](../debugger/remote-debugging-errors-and-troubleshooting.md)