---
title: "Source des informations de contrôle d’exécution | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9647f1f399b0d6516fe6475e6245c6834a0ea2b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-runtime-details"></a>Détails de l’exécution contrôle source
Un projet est ajouté au contrôle de code source lorsque l’utilisateur ajoute un fichier dans le projet de contrôle de code source, ou par un contrôleur automation, par exemple un Assistant. Un projet ne spécifie pas de proprement dit qu’il est sous contrôle de code source ; Il prend en charge le contrôle de code source, mais doit être ajouté manuellement à ce dernier.  
  
## <a name="registering-with-a-source-control-package"></a>L’inscription auprès d’un Package de contrôle de code Source  
 Lorsqu’un fichier dans votre projet est ajouté au contrôle de code source, l’environnement appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> afin de vous fournir quatre chaînes opaques qui sont utilisés en tant que les cookies par le système de contrôle de code source. Stocker ces chaînes dans votre fichier projet. Ces chaînes qui doivent être passées au Stub de contrôle de Source (le composant de Visual Studio qui gère les packages de contrôle de code source) au démarrage du type de projet en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>. À son tour charge le package de contrôle de source appropriée il transfère l’appel à son implémentation de `IVsSccManager2::RegisterSccProject`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Prise en charge du contrôle de code source](../../extensibility/internals/supporting-source-control.md)