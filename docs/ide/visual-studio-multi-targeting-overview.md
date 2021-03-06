---
title: "Vue d’ensemble du multiciblage Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
ms.assetid: b1702c33-0672-4ebc-b779-2b324d6ea880
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ad2917a1cf0a620f2e228828a152d91ec8948734
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-multi-targeting-overview"></a>Vue d’ensemble du multiciblage Visual Studio
Dans cette version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous pouvez spécifier la version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] exigée pour votre application. Par conséquent, si vous souhaitez utiliser cette version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour continuer à développer un projet démarré dans une version antérieure, il n’est pas nécessaire de changer la cible du Framework. Vous pouvez également créer une solution contenant des projets qui ciblent différentes versions du Framework. Le ciblage du Framework permet aussi de garantir que l’application utilise uniquement les fonctionnalités disponibles dans la version spécifiée du Framework.  
  
> [!TIP]
>  Vous pouvez également cibler des applications pour différentes plateformes. Pour plus d’informations, consultez [Multiciblage](../msbuild/msbuild-multitargeting-overview.md).  
  
## <a name="framework-targeting-features"></a>Fonctionnalités du ciblage du Framework  
 Le ciblage du Framework inclut les fonctionnalités suivantes :  
  
-   Quand vous ouvrez un projet qui cible une version antérieure de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] peut automatiquement le mettre à niveau ou laisser la cible telle quelle.  
  
-   Quand vous créez un projet, vous pouvez spécifier la version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que vous voulez cibler.  
  
-   Vous pouvez modifier la version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que cible un projet existant.  
  
-   Vous pouvez cibler une version différente du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] dans chacun des différents projets de la même solution.  
  
-   Quand vous modifiez la version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ciblée par un projet, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] applique les modifications obligatoires aux références et aux fichiers de configuration.  
  
 Quand vous travaillez sur un projet qui cible une version antérieure du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio change dynamiquement l’environnement de développement, de la façon suivante :  
  
-   Il filtre les éléments des boîtes de dialogue **Nouveau projet**, **Ajouter un nouvel élément**, **Ajouter une nouvelle référence** et **Ajouter une référence de service** de façon à omettre les choix qui ne sont pas disponibles dans la version ciblée.  
  
-   Il filtre les contrôles personnalisés de la **boîte à outils** pour supprimer ceux qui ne sont pas disponibles dans la version ciblée et pour afficher la version la plus récente quand plusieurs contrôles sont disponibles.  
  
-   Il filtre IntelliSense de façon à omettre les fonctionnalités de langage qui ne sont pas disponibles dans la version ciblée.  
  
-   Il filtre les propriétés de la fenêtre **Propriétés** de façon à omettre celles qui ne sont pas disponibles dans la version ciblée.  
  
-   Il filtre les options de menu de façon à omettre celles qui ne sont pas disponibles dans la version ciblée.  
  
-   Pour les builds, il utilise la version du compilateur et les options de compilateur appropriées pour la version ciblée.  
  
> [!NOTE]
>  Le ciblage du Framework ne garantit pas que votre application s’exécutera correctement. Vous devez tester votre application pour vous assurer qu’elle s’exécute sur la version ciblée. Vous ne pouvez pas cibler des versions du Framework antérieures à .NET Framework 2.0.  
  
## <a name="selecting-a-target-framework-version"></a>Sélection d’une version du Framework cible  
 Quand vous créez un projet, sélectionnez la version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] cible dans la boîte de dialogue **Nouveau projet**. La liste des modèles de projet disponibles est filtrée selon vos sélections. Dans un projet existant, vous pouvez modifier la version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] cible dans la boîte de dialogue Propriétés du projet. Pour plus d’informations, consultez [Guide pratique pour cibler une version du .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
> [!NOTE]
>  Dans les éditions Express de Visual Studio, vous ne pouvez pas définir la version du Framework cible dans la boîte de dialogue **Nouveau projet**.  
  
## <a name="resolving-system-and-user-assembly-references"></a>Résolution des références système et d’assembly utilisateur  
 Pour cibler une version du .Net Framework, vous devez d’abord installer les références d’assembly appropriées. Les références d’assembly pour les versions 2.0, 3.0 et 3.5 du .NET Framework sont incluses dans .NET Framework 3.5 SP1, que vous pouvez télécharger à partir du site web du [Centre de téléchargement Microsoft, Microsoft Visual Studio](http://go.microsoft.com/fwlink/?LinkId=227602). Les références d’assembly pour .NET Framework 3.5 Client Profile, .NET Framework 4, .NET Framework 4 Client Profile et Silverlight sont également disponibles à partir du site web des [téléchargements de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=179687).  
  
> [!NOTE]
>  .NET Framework Client Profile est un sous-ensemble du .NET Framework qui fournit un ensemble limité de bibliothèques et de fonctionnalités. Pour plus d’informations sur les profils clients, consultez [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).  
  
 La boîte de dialogue **Ajouter une référence** désactive les assemblys système qui ne se rapportent pas à la version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] cible afin qu’ils ne puissent pas être ajoutés à un projet par inadvertance. (Les assemblys système sont des fichiers .dll inclus dans une version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].) Les références qui appartiennent à une version du Framework ultérieure à la version ciblée ne seront pas résolues, et les contrôles qui dépendent d’une telle référence ne peuvent pas être ajoutés. Si vous voulez activer une telle référence, réinitialisez la cible du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] du projet sur une cible qui inclut la référence.  Pour plus d’informations, consultez [Guide pratique pour cibler une version du .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
 Pour plus d’informations sur les références d’assembly, consultez [Résolution d’assemblys au moment du design](../msbuild/resolving-assemblies-at-design-time.md).  
  
## <a name="enabling-linq"></a>Activation de LINQ  
 Quand vous ciblez .NET Framework 3.5 ou une version ultérieure, une référence à System.Core et une importation au niveau du projet pour System.Linq (en Visual Basic uniquement) sont automatiquement ajoutées. Si vous voulez utiliser les fonctionnalités LINQ, vous devez également activer Option Infer (en Visual Basic uniquement). La référence et l’importation sont automatiquement supprimées si vous faites passer la version du .NET Framework à une version antérieure. Pour plus d’informations, consultez [Utilisation de LINQ](/dotnet/csharp/tutorials/working-with-linq).  
  
## <a name="see-also"></a>Voir aussi  
 [Multiciblage](../msbuild/msbuild-multitargeting-overview.md)   
 [Compatibilité de la plateforme et configuration requise](http://www.microsoft.com/visualstudio/eng/products/compatibility)