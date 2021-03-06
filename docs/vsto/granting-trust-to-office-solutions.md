---
title: "Accorder la confiance à des Solutions Office | Documents Microsoft"
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
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
ms.assetid: 6c33e614-d367-4556-9e76-0f302ad0f929
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: da7f4695bc817a66761c579b4c5af85b59ee041f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="granting-trust-to-office-solutions"></a>Octroi de niveaux de confiance à des solutions Office
  L’octroi de confiance aux solutions Office signifie que la modification de la stratégie de sécurité de chaque ordinateur cible pour approuver l’assembly de solution, le manifeste d’application, le manifeste de déploiement et le document. Approbation peut être accordée à la solution Office par vous ou l’utilisateur final.  
  
 Vous pouvez accorder une confiance totale à la solution Office en signant les manifestes d’application et de déploiement.  
  
 Les utilisateurs finaux peuvent accorder une confiance à la solution Office en effectuant une décision d’approbation dans le [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] invite d’approbation.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a>Approbation de la Solution par l’Application et déploiement de la signature de manifestes  
 Manifestes d’application et déploiement pour Office solutions doivent être signées avec un certificat qui identifie le serveur de publication. Les certificats fournissent une base pour les décisions d’approbation.  
  
 Un certificat temporaire est créé pour vous et approuvé au moment de la génération afin que la solution s’exécute pendant que vous le déboguez. Si vous publiez une solution qui est signée avec un certificat temporaire, l’utilisateur final sera invité à prendre une décision d’approbation.  
  
 Si vous vous connectez à la solution avec un certificat connu et approuvé, la solution sera automatiquement installée sans solliciter l’utilisateur final à prendre une décision d’approbation. Pour plus d’informations sur la façon d’obtenir un certificat de signature, consultez [ClickOnce et Authenticode](/visualstudio/deployment/clickonce-and-authenticode). Une fois un certificat obtenu, le certificat doit être approuvé explicitement en l’ajoutant à la liste des éditeurs approuvés. Pour plus d’informations, consultez [Comment : ajouter un éditeur approuvé à un ordinateur Client pour les Applications ClickOnce](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications).  
  
 Si un développeur signe la solution avec un certificat temporaire, un administrateur peut signer à nouveau la personnalisation avec un certificat connu et approuvé à l’aide de la Manifest Generation and Editing Tool (mage.exe), qui est un des outils de Microsoft .NET Framework. Pour plus d’informations sur la signature des solutions, consultez [Comment : signe des Solutions Office](../vsto/how-to-sign-office-solutions.md) et [Comment : signer Application et les manifestes de déploiement](/visualstudio/ide/how-to-sign-application-and-deployment-manifests).  
  
##  <a name="TrustPrompt"></a>Approbation de la Solution à l’aide de l’invite d’approbation ClickOnce  
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]invite l’utilisateur final à prendre une décision d’approbation s’il n’existe aucune stratégie de l’entreprise qui approuve le certificat de la solution. Si l’utilisateur final approuve la solution, une entrée de liste d’inclusion est créée qui contient une URL et une clé publique pour stocker cette décision d’approbation. Lorsqu’une personnalisation approuvée est exécutée ultérieurement, l’utilisateur final n’est pas invité à nouveau.  
  
 Les administrateurs peuvent désactiver la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] invite d’approbation ou exiger que l’invite de commandes se produisent uniquement pour les solutions qui sont signées avec un certificat Authenticode. Pour plus d’informations sur la façon de modifier ces paramètres pour les zones MyComputer, LocalIntranet, Internet, TrustedSites et UntrustedSites, consultez [Comment : configurer le comportement d’invite approbation ClickOnce](/visualstudio/deployment/how-to-configure-the-clickonce-trust-prompt-behavior).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation des Solutions Office](../vsto/securing-office-solutions.md)   
 [Accorder la confiance à des Documents](../vsto/granting-trust-to-documents.md)   
 [Résolution des problèmes de sécurité des solutions Office](../vsto/troubleshooting-office-solution-security.md)   
 [Considérations spécifiques sur la sécurité pour les solutions Office](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  