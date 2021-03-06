---
title: "Développement collaboratif de Solutions Office | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
ms.assetid: c493354b-17d3-4e50-85f0-968b104bc978
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 94313e1e7cb8d6f36c5c8bfb505d280f4e235a3b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="collaborative-development-of-office-solutions"></a>Développement collaboratif de solutions Office
  Plusieurs développeurs peuvent travailler sur un projet Office de la même façon qu’ils collaborent sur d’autres projets Visual Studio. Visual Studio localise correctement l’installation de Microsoft Office sur chaque ordinateur, même si Office est installé dans des emplacements différents. Toutefois, il existe certaines considérations importantes à connaître.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="debug-properties-are-not-shared"></a>Déboguer propriétés ne sont pas partagées.  
 Les propriétés de débogage ne sont pas partagées entre plusieurs utilisateurs sous contrôle de code source. Projets Visual Basic et Visual c# stockent les propriétés de débogage dans un fichier spécifique à l’utilisateur (*nom_projet*. vbproj.user ou *nom_projet*. csproj.user), et ce fichier n’est pas sous contrôle de code source. Si plusieurs personnes effectuent un débogage, chacune d'entre elles doit entrer manuellement les propriétés de débogage.  
  
 Si le projet est hébergé sur un partage réseau au lieu de contrôle de code source, certaines étapes supplémentaires doivent être prises pour permettre aux développeurs travaillant en collaboration ouvrir la solution et de tester l’assembly.  
  
## <a name="source-control-requires-checking-out-all-files"></a>Requiert de l’extraction de tous les fichiers de contrôle de code source  
 Si vous utilisez le contrôle de code source pour vos projets, vous devez extraire tous les fichiers sous un fichier de code dans **l’Explorateur de solutions** (par exemple, les fichiers de code ThisAddIn, ThisWorkbook ou ThisDocument) chaque fois que vous modifiez le fichier de code, même les fichiers qui sont masqués par défaut. Si vous ne découvrez que le fichier de code de niveau supérieur, vos modifications peuvent être perdues.  
  
 Après avoir apporté vos modifications, archiver tous les fichiers. Pour plus d’informations sur les fichiers de code masqué dans les projets, consultez [les projets Office dans l’environnement Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="security-for-informal-collaboration-on-a-network"></a>Sécurité pour une Collaboration informelle sur un réseau  
 Pour toutes les solutions au niveau du document qui se trouvent dans un emplacement réseau (tel que \\ \\ *nom_serveur*\\*nom_partage*), l’emplacement qualifié complet doit être ajouté à la liste des dossiers approuvés dans l’application Microsoft Office que vous utilisez. Sélectionnez l’option pour inclure les sous-répertoires sous le dossier principal, ou plus précisément en ajoutez debug et créer des dossiers à la liste des dossiers approuvés. Pour plus d’informations, consultez [l’octroi de confiance à des Documents](../vsto/granting-trust-to-documents.md).  
  
 Les certificats temporaires qui sont générés automatiquement au moment de la génération ne sont pas assurées par les mots de passe. Les certificats contiennent le nom de connexion du développeur et d’autres informations personnelles. Si vous déployez des personnalisations qui sont signées par des certificats temporaires, il se peut que d’autres peuvent être en mesure d’accéder à ces informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation des Solutions Office](../vsto/securing-office-solutions.md)   
 [Conception et création de Solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Génération de solutions Office](../vsto/building-office-solutions.md)  
  
  