---
title: "Comment : déclencher des événements lorsque l’éditeur perd le Focus | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9a566d52dc1aabb9895e2f1f9751fdb37ae016d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Comment : déclencher des événements lorsque l’éditeur perd le Focus
Il est parfois nécessaire de savoir quand un éditeur perd le focus sur le frame de fenêtre. Par exemple, vous devrez peut-être extraire du code à partir d’une fenêtre de code une fois que l’éditeur de focus n’est plus sur ce dernier. La procédure suivante fournit les étapes à suivre pour recevoir une notification de l’éditeur perd le focus.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Pour déclencher un événement en réponse à un éditeur perd le focus  
  
1.  Surveiller les événements de sélection en obtenant un <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> à partir de l’objet <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> et fournir votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> objet.  
  
3.  Dans votre appel à <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, recherchez `elementid==SEID_WindowFrame`.  
  
4.  Test du `varValueNew` paramètre pour deux choses :  
  
    1.  Le frame de fenêtre que vous recherchez.  
  
    2.  Le point auquel votre programme perd la sélection pour ce frame de fenêtre.