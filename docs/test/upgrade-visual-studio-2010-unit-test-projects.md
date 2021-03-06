---
title: "Mettre à niveau des projets de tests unitaires dans Visual Studio 2010 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1502b51-d6db-4894-9fbf-4a5723e4bb1a
caps.latest.revision: 8
ms.author: douge
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: d6550f2aa1aab249eda569ff84ddf4dcf488aa18
ms.contentlocale: fr-fr
ms.lasthandoff: 05/13/2017

---
# <a name="upgrade-visual-studio-2010-unit-test-projects"></a>Mettre à niveau des projets de tests unitaires dans Visual Studio 2010
[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] inclut la compatibilité des projets de test avec les projets de test [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1. Par exemple, les projets de test que vous avez créés avec [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 peuvent être ouverts avec [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] sans aucune mise à niveau. Votre équipe peut donc utiliser à la fois [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 et [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] pour travailler sur le même projet de test. Pour plus d’informations, consultez [Mise à niveau de tests de Visual Studio 2010](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52).  
  
 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] introduit plusieurs changements pour les tests unitaires. En raison de ces changements, il est important de comprendre les problèmes de compatibilité entre les versions précédentes de Visual Studio et [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]. Parmi les changements apportés aux tests unitaires, l’un d’eux est particulièrement important : [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] comprend plusieurs modèles de projets de test, notamment un modèle de projet de test unitaire. De nouveaux tests unitaires ont été ajoutés au nouveau modèle de projet de test unitaire. Les tests unitaires peuvent également être inclus dans un autre nouveau modèle de projet de test appelé modèle de projet de test codé de l’interface utilisateur. Pour plus d’informations sur les nouveaux modèles de projet de test, consultez [Mise à niveau des tests à partir de versions antérieures de Visual Studio](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52). Les nouveaux projets de test unitaires n’incluent plus un fichier de paramètres de test par défaut. Grâce à l’exclusion du fichier de paramètres de test, les performances de vos tests unitaires s’améliorent. Pour des raisons de compatibilité, vous pouvez continuer à utiliser les projets de test existants que vous avez créés à l’aide de Visual Studio 2010. Toutefois, pour des raisons de performances, nous vous recommandons de supprimer le fichier de paramètres de test associé au projet de test, sauf si vous avez spécifiquement besoin du fichier de paramètres de test. Par exemple, vous pouvez choisir de conserver le fichier de paramètres de test si vos tests unitaires s’exécutent dans un environnement distribué, ou si vous devez collecter des données de diagnostic spécifiques. Si vous avez un besoin similaire avec le nouveau modèle de projet de test unitaire ou le modèle de projet de test codé de l’interface utilisateur, vous pouvez également leur ajouter manuellement un fichier de paramètres de test.  
  
> [!NOTE]
>  Les tests unitaires existants de vos projets de test [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 fonctionnent sans montrer de discontinuité entre [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 et [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]. Aucune modification n’est apportée aux fichiers projet de test quand un projet de test Visual Studio 2010 contenant vos tests unitaires est ouvert dans [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], ou vice versa.  
  
> [!CAUTION]
>  Visual Studio 2010 ne peut pas ouvrir un projet C++/CLI qui cible l’ensemble d’outils version 11.0, c’est-à-dire un projet créé dans Visual Studio 2012. Cette restriction s’applique à tous les projets C++/CLI, et pas seulement aux projets de test unitaire C++/CLI.  
  
> [!NOTE]
>  Vous pouvez exécuter les nouveaux tests unitaires via vstest.console.exe à partir de la ligne de commande. Pour plus d’informations sur l’utilisation de vstest.console.exe, consultez [Options de ligne de commande VSTest.Console.exe](/devops-test-docs/test/vstest-console-exe-command-line-options), ou exécutez la commande à l’aide du commutateur d’aide : **vstest.console.exe /?**. Vous pouvez continuer à exécuter vos tests unitaires existants à l’aide de MStest.exe. Pour plus d’informations, consultez [Exécuter des tests automatisés à partir de la ligne de commande à l’aide de MSTest](/devops-test-docs/test/run-automated-tests-from-the-command-line-using-mstest) et [Options de ligne de commande MSTest.exe](/devops-test-docs/test/mstest-exe-command-line-options).  
  
 Le nouvel Explorateur de tests représente un autre changement important. Dans [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], certaines fenêtres de tests auxquelles vous étiez peut-être habitué depuis la version antérieure de Visual Studio sont maintenant dépréciées, par exemple la fenêtre Affichage des tests. L’Explorateur de tests est conçu pour mieux prendre en charge les développeurs et les équipes qui intègrent des tests unitaires à leurs pratiques de développement de logiciels. Pour plus d’informations, consultez [Exécuter des tests unitaires avec l’Explorateur de tests](../test/run-unit-tests-with-test-explorer.md).  
  
## <a name="compatibility-issues-between-visual-studio-2010-sp1-and-visual-studio-2012"></a>Problèmes de compatibilité entre Visual Studio 2010 SP1 et Visual Studio 2012  
 Voici quelques aspects à prendre en compte pour la migration de tests unitaires entre Visual Studio 2010 SP1 et [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] :  
  
|Fonctionnalité de test unitaire|Problème|Solution|  
|-----------------------------|-----------|--------------|  
|Les listes de tests (fichiers .vsmdi) sont dépréciées dans [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|Vous ne pourrez plus créer de listes de tests (fichiers .vsmdi), ni exécuter de listes de tests à partir de Visual Studio. **Conseil :** Les catégories de test offrent plus de souplesse que la fonctionnalité des listes de tests des versions antérieures de Microsoft Visual Studio. Vous pouvez utiliser des opérateurs logiques avec les catégories de test pour exécuter des tests à partir de plusieurs catégories ou pour limiter les tests que vous exécutez à des tests qui appartiennent à plusieurs catégories. Les catégories de test sont également faciles à ajouter lors de la création de vos méthodes de test et vous n'avez pas besoin de gérer des listes de tests après la création. Avec les catégories de test, vous n’avez pas besoin d’archiver et d’extraire le fichier **\<nom_solution>.vsmdi** qui gère les listes de tests. Pour plus d’informations, consultez [Définition de catégories de test pour regrouper vos tests](/devops-test-docs/test/defining-test-categories-to-group-your-tests).|- Pour maintenir la compatibilité avec les projets de test existants qui utilisent des listes de tests, vous pouvez toujours modifier les fichiers .vsmdi à l’aide de Visual Studio.<br />- Bien que vous ne puissiez pas exécuter les listes de tests migrées à partir de Visual Studio, vous pouvez toujours les exécuter par l’intermédiaire de mstest.exe à partir de la ligne de commande. Pour plus d’informations, consultez [Exécuter des tests automatisés à partir de la ligne de commande à l’aide de MSTest](/devops-test-docs/test/run-automated-tests-from-the-command-line-using-mstest)<br />- Si vous utilisiez une liste de tests dans votre définition de build, vous pouvez continuer à l’utiliser. Pour plus d’informations, consultez [Guide pratique pour configurer et exécuter des tests planifiés après la génération de votre application](http://msdn.microsoft.com/en-us/32acfeb1-b1aa-4afb-8cfe-cc209e6183fd) et [Exécuter des tests dans votre processus de génération](http://msdn.microsoft.com/Library/d05743a1-c5cf-447e-bed9-bed3cb595e38).|  
|Les accesseurs privés sont dépréciés dans [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].<br /><br /> Dans les versions précédentes de Visual Studio, vous pouviez utiliser Publicize pour spécifier des interfaces de programmation d’applications (API) internes et créer des API de contrepartie publiques que vous pouviez appeler dans vos tests, pour appeler ensuite les API internes de votre produit. Vous pouviez ensuite utiliser la génération de code pour créer des stubs de test et générer un extrait de code à l’intérieur de ce stub.|Il n’est plus possible de créer des accesseurs privés.|<ul><li>Les projets de test Visual Studio 2010 sont compilés et utilisables dans [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]. La build inclut des avertissements de sortie.</li><li>Si vous avez encore besoin de tester des API internes, vous avez les options suivantes :<br /><br /> <ul><li>Utilisez la classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> pour vous aider à accéder aux API internes et privées dans votre code. Elle se trouve dans l’assembly Microsoft.VisualStudio.QualityTools.UnitTestFramework.dll.</li><li>Créez un framework de réflexion capable de refléter votre code pour accéder aux API internes ou privées.</li><li>Si le code auquel vous essayez d’accéder est interne, vous pouvez éventuellement accéder à vos API par l’intermédiaire de <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> pour que votre code de test ait accès aux API internes.</li></ul></li></ul>|  
|Impact des tests supprimé|||  
|Partage des résultats de l’exécution via les journaux TRX à partir de l’Explorateur de tests.||Vous pouvez toujours obtenir les journaux TRX à partir de la ligne de commande et de Team Build.|  
  
## <a name="see-also"></a>Voir aussi  
 [Portage, migration et mise à niveau des projets Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)   
 [Tests unitaires sur votre code](../test/unit-test-your-code.md)   
 [Mise à niveau des tests à partir de versions antérieures de Visual Studio](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)   
 [Mise à niveau de tests codés de l’interface utilisateur à partir de Visual Studio 2010](../test/upgrading-coded-ui-tests-from-visual-studio-2010.md)

