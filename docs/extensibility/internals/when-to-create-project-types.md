---
title: "Quand créer des Types de projet | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b532ad4e72fb15cd9409c362259347f6f3833d2e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="when-to-create-project-types"></a>Quand créer des Types de projets
Création d’un nouveau type de projet fournit une base pour la personnalisation [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour vos utilisateurs. Toutefois, la création d’un nouveau type de projet n’est pas requis pour tous les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] personnalisations. Les instructions suivantes doivent vous aider à déterminer si un nouveau type de projet est requis pour votre scénario.  
  
## <a name="create-a-new-project-type"></a>Créer un nouveau Type de projet  
 Vous devez créer un type de projet si vous souhaitez personnaliser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à agir dans un ou plusieurs des manières suivantes :  
  
-   Dans la génération, déploiement, configurations et contrôle de code source.  
  
-   Offre la prise en charge le débogage.  
  
-   Afficher les éléments de projet dans **l’Explorateur de solutions**.  
  
-   Utilisez le **ouvrir le projet** ou **nouveau projet** boîte de dialogue.  
  
-   Prend en charge l’imbrication de projet.  
  
## <a name="extend-an-existing-project-type"></a>Étendre un Type de projet existant  
 Vous souhaiterez peut-être créer un nouveau type de projet que vous pouvez utiliser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comme suit pour modifier ou étendre le comportement d’un type de projet existant, par exemple, en modifiant le processus de génération pour [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projets :  
  
-   Comme une seule unité de travail avec plusieurs fichiers.  
  
-   Afficher un seul fichier en tant que hiérarchie de sous-éléments.  
  
-   Afficher un contexte de commande autour d’éditeurs.  
  
-   Afficher un contexte de service pour les éditeurs.  
  
## <a name="use-an-existing-project-type"></a>Utiliser un Type de projet existant  
 Création d’un projet n’est parfois pas nécessaire. Le tableau suivant répertorie les tâches que vous n’êtes pas obligé de créer un type de projet pour.  
  
|Tâche|Description|  
|----------|-----------------|  
|Gestion des commandes|Un VSPackage peut gérer les commandes.|  
|Création d’un éditeur|Éditeurs personnalisés peuvent être inscrits. Pour plus d’informations, consultez [les éditeurs et les fenêtres de Document](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc).|  
|Propriétaire de windows|Vous pouvez créer des fenêtres Outil et document sans ajouter un nouveau type de projet.|  
|Exposition de propriétés dans la fenêtre Propriétés|Tous les objets peuvent exposer des propriétés.|  
  
## <a name="create-a-project-subtype"></a>Créer un sous-type de projet  
 Vous pouvez utiliser des sous-types de projet pour étendre un type de projet managé sans avoir à créer un nouveau type de projet. Sous-types de projet permettent d’agrégation de COM d’étendre des projets managés écrits dans Microsoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ou [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Avec l’agrégation de COM, vous pouvez réutiliser une grande partie de l’implémentation de système de projet managé et toujours personnaliser pour un scénario particulier par le biais d’agrégation et l’utilisation de la prise en charge des interfaces. Pour plus d’informations sur les sous-types de projet, consultez [sous-types de projet](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Les éditeurs et les fenêtres de document](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc)   
 [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)