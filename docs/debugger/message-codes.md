---
title: Codes de message | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7a1e724c5c328c86398c43263b19980b5f464a39
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="message-codes"></a>Codes des messages
Chaque ligne de message affichée dans [vue Messages](../debugger/messages-view.md) contient « P », de,' de,' ou le code de « R ». Ces codes ont les significations suivantes :  
  
|Code|Signification|  
|----------|-------------|  
|P|Le message a été publié vers la file d’attente avec le **PostMessage** (fonction). Aucune information n’est disponible concernant la disposition finale du message.|  
|S|Le message a été envoyé avec les **SendMessage** (fonction). Cela signifie que l’expéditeur ne reprend pas le contrôle jusqu'à ce que le destinataire traite et retourne le message. Le récepteur peut, par conséquent, passer une valeur de retour à l’expéditeur.|  
|s|Le message a été envoyé, mais la sécurité empêche l’accès à la valeur de retour.|  
|R|Chaque ' a une ligne « R » (retour) correspondante qui répertorie la valeur de retour du message. Parfois, les appels de message sont imbriquées, ce qui signifie que ce gestionnaire d’un message envoie un autre message.|