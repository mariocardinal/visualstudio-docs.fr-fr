---
title: "Impossible de s’attacher au processus | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.remote.unable2attach
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0468de6c-3ff1-4979-a8c6-8afb53f37547
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ec2c181edc69ac2e693de96fcf72fe9116f758b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="unable-to-attach-to-the-process"></a>Impossible de s'attacher au processus
Impossible de s'attacher au processus Le composant Débogueur sur le serveur s'est vu refuser l'accès pendant la connexion à cet ordinateur.  
  
 Deux scénarios courants peuvent être à l'origine de cette erreur :  
  
 **Scénario 1 :** ordinateur A exécute Windows XP. L'ordinateur B exécute Windows Server 2003. Le registre de l'ordinateur B contient la valeur DWORD suivante :  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 L'utilisateur 1 démarre une session Terminal Server (session 1) sur l'ordinateur B et démarre une application managée à partir de cette session.  
  
 L’utilisateur 2, qui est administrateur sur les deux ordinateurs, connecté à l’ordinateur A. À partir de là, il ou elle essaie de s’attacher à une application en cours d’exécution dans la session 1 sur l’ordinateur B.  
  
 **Scénario 2 :** un utilisateur est connecté sur deux ordinateurs, A et B, dans le même groupe de travail à l’aide du mot de passe sur les deux ordinateurs. Le débogueur est en cours d’exécution sur l’ordinateur A et tente d’attacher à une application managée qui s’exécute sur l’ordinateur B. **accès réseau : modèle de partage et de sécurité pour les comptes locaux** la valeur **invité**.  
  
### <a name="to-solve-scenario-1"></a>Pour résoudre le scénario 1  
  
-   Exécutez le débogueur et l'application managée avec le même nom de compte d'utilisateur et le même mot de passe.  
  
### <a name="to-solve-scenario-2"></a>Pour résoudre le scénario 2  
  
1.  À partir de la **Démarrer** menu, choisissez **le panneau de configuration**.  
  
2.  Dans le panneau de configuration, double-cliquez sur **outils d’administration**.  
  
3.  Dans la fenêtre Outils d’administration, double-cliquez sur **stratégie de sécurité locale**.  
  
4.  Dans la fenêtre Stratégie de sécurité locale, sélectionnez **stratégies locales**.  
  
5.  Dans le **stratégies** colonne, double-cliquez sur **accès réseau : modèle de partage et de sécurité pour les comptes locaux**.  
  
6.  Dans le **accès réseau : modèle de partage et de sécurité pour les comptes locaux** boîte de dialogue, changez le paramètre de sécurité local à **classique**, puis cliquez sur **OK**.  
  
    > [!CAUTION]
    >  Changer le modèle de sécurité en Classique peut engendrer un accès inattendu à des fichiers partagés et aux composants DCOM. Si vous apportez cette modification, un utilisateur distant peut s'authentifier avec votre compte d'utilisateur local plutôt qu'avec un compte Invité. Si un utilisateur distant utilise votre nom d'utilisateur et mot de passe, celui-ci est capable d'accéder à tout dossier ou objet DCOM que vous partagez. Si vous utilisez ce modèle de sécurité, veillez à ce que tous les comptes d'utilisateur sur l'ordinateur utilisent des mots de passe forts ou configurez un îlot de réseau isolé pour les ordinateurs de débogage et les ordinateurs débogués afin d'éviter les risques d'accès non autorisé.  
  
7.  Fermez toutes les fenêtres.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)