---
title: "Spécifiant l’emplacement du fichier de VSPackage à l’interpréteur de commandes de Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b987d5e88bcbcf02bfd80ddf5c3ed0d67a149b53
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Spécifiant l’emplacement du fichier de VSPackage à l’interpréteur de commandes de Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]doit être en mesure de trouver la DLL à charger le VSPackage d’assembly. Vous pouvez le rechercher de différentes manières, comme décrit dans le tableau suivant.  
  
|Méthode|Description|  
|------------|-----------------|  
|Utilisez la clé de Registre de base de code.|La clé de la base de code peut être utilisée pour diriger [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour charger l’assembly VSPackage à partir de n’importe quel chemin de fichier qualifié complet. La valeur de la clé doit être le chemin d’accès de fichier à la DLL. Ceci est le meilleur moyen d’avoir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de charger l’assembly de votre package. Cette technique est parfois appelée « CodeBase/privée installation active technique. » Lors de l’enregistrement la valeur de la base de code est passée pour les classes d’attributs d’inscription via une instance de la <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> type.|  
|Placer la DLL dans le **PrivateAssemblies** active.|Placez l’assembly dans le **PrivateAssemblies** sous-répertoire de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] active. Assemblys situés dans **PrivateAssemblies** sont détectées automatiquement, mais ne sont pas visibles dans le **ajouter des références** boîte de dialogue. La différence entre **PrivateAssemblies** et **PublicAssemblies** est que les assemblys dans **PublicAssemblies** sont énumérées dans le **ajouter des références**  boîte de dialogue. Si vous choisissez de ne pas utiliser la technique « répertoire d’installation CodeBase/privée », vous devez l’installer dans le **PrivateAssemblies** active.|  
|Utiliser un assembly avec nom fort et la clé de Registre d’Assembly.|La clé de l’Assembly peut être utilisée pour indiquer explicitement [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour charger un nom fort nommé assembly VSPackage. La valeur de la clé doit être le nom fort de l’assembly.|  
|Placer la DLL dans le **PublicAssemblies** active.|Enfin, l’assembly peut également être placé dans le **PublicAssemblies** sous-répertoire. Assemblys situés dans **PublicAssemblies** sont détectées automatiquement et apparaît également dans le **ajouter des références** boîte de dialogue de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].<br /><br /> Les assemblys VSPackage doivent uniquement être placés dans le **PublicAssemblies** répertoire s’ils contiennent géré des composants qui sont destinés à être réutilisé par d’autres développeurs VSPackage. La plupart des assemblys ne répondent pas à ce critère.|  
  
> [!NOTE]
>  Utiliser des assemblys avec nom fort, signés pour tous vos assemblys dépendants. Ces assemblys doivent également être installés dans votre propre répertoire ou dans le global assembly cache (GAC). Cela empêche les conflits avec les assemblys qui ont le même nom de fichier de base, appelé liaison de nom de faible.