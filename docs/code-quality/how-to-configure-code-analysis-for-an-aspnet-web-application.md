---
title: "Comment : configurer l’analyse du Code pour une Application Web ASP.NET | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dbc2ba8f78cc8f38bce62adbd3d91604875bffa3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Comment : configurer l'analyse du code pour une application Web ASP.NET
Dans [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] et [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)] vous pouvez sélectionner dans une liste d’analyse du Code *ensembles de règles* à appliquer au [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] application Web. L’ensemble de règles par défaut est de règles Microsoft intitule recommandées. Vous pouvez sélectionner un autre ensemble de règles à appliquer au site Web.  
  
### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>Pour configurer un ensemble de règles pour un projet d'infrastructure de page ASP.NET  
  
1.  Sélectionnez le site Web dans **l’Explorateur de solutions**.  
  
2.  Sur le **analyser** menu, cliquez sur **configurer l’analyse du Code pour le Site Web**.  
  
3.  Si vous avez sélectionné la solution et la solution comporte plusieurs projets, sélectionnez le build cible et configuration de système d’exploitation le **Configuration** et **plateforme** répertorie.  
  
4.  Pour chaque projet dans la solution, cliquez sur le **l’ensemble de règles** colonne, puis cliquez sur le nom de la règle est configuré pour s’exécuter.  
  
5.  Par défaut, l’analyse du code est exécutée sur tous les projets dans la solution. Pour désactiver ou activer l’analyse du code pour un projet particulier, procédez comme suit :  
  
    1.  Cliquez sur le nom du projet, puis sur Propriétés.  
  
    2.  Activez ou désactivez le **activer l’analyse du Code** case à cocher. Vous pouvez également exécuter l’analyse du code manuellement en sélectionnant **exécuter l’analyse du Code sur le Site Web** à partir de la **analyser** menu.  
  
6.  Dans le **exécuter cet ensemble de règles** déroulante liste, procédez comme suit :  
  
    -   Sélectionnez l’ensemble de règles que vous souhaitez utiliser.  
  
    -   Sélectionnez  **\<Parcourir >** pour spécifier une règle personnalisée existante du jeu qui n’est pas dans la liste.  
  
    -   Définissez un ensemble de règles personnalisé. Pour plus d’informations, consultez [création d’ensembles de règles personnalisés](../code-quality/creating-custom-code-analysis-rule-sets.md).