---
title: Arguments de ligne de commande pour Help Content Manager | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3aa9890a-1147-42ba-adea-17935d184038
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 33a4573a901de65cc203a7b8f5c18c88557af42e
ms.contentlocale: fr-fr
ms.lasthandoff: 05/13/2017

---
# <a name="command-line-arguments-for-the-help-content-manager"></a>Arguments de ligne de commande pour Help Content Manager
Vous pouvez spécifier la façon de déployer et de gérer le contenu d’aide locale à l’aide d’arguments de ligne de commande pour Help Content Manager (HlpCtntmgr.exe). Vous devez exécuter des scripts pour cet outil en ligne de commande avec des autorisations d’administrateur, et vous ne pouvez pas exécuter ces scripts en tant que service. Vous pouvez effectuer les tâches suivantes à l’aide de cet outil :  
  
-   Ajouter ou mettre à jour le contenu d’aide locale à partir d’un disque ou du cloud.  
  
-   Supprimer le contenu d’aide locale.  
  
-   Déplacer le magasin de contenu d’aide locale.  
  
-   Ajouter, mettre à jour, supprimer ou déplacer le contenu d’aide locale en mode silencieux.  
  
 Syntaxe :  
  
```  
HlpCtntmgr.exe /operation Value /catalogname CatalogName /locale Locale /sourceuri InstallationPoint  
```  
  
 Par exemple :  
  
```  
hlpctntmgr.exe /operation install /catalogname VisualStudio14 /locale en-us /sourceuri d:\productDocumentation\HelpContentSetup.msha  
```  
  
## <a name="switches-and-arguments"></a>Commutateurs et arguments  
 Le tableau suivant définit les commutateurs et les arguments que vous pouvez utiliser pour l’outil en ligne de commande pour Help Content Manager :  
  
|Basculer|Obligatoire ?|Arguments|  
|------------|---------------|---------------|  
|/operation|Oui|-   **Install** : ajoute des livres de la source d’installation spécifiée dans le magasin de contenu local.<br />     Ce commutateur requiert l’argument /booklist, l’argument /sourceURI, ou les deux. Si vous ne spécifiez pas l’argument /sourceURI, l’URI de Visual Studio par défaut est utilisé comme source d’installation. Si vous ne spécifiez pas l’argument /booklist, tous les livres sur /sourceUri sont installés.<br />-   **Uninstall** : supprime les livres que vous spécifiez dans le magasin de contenu local.<br />     Ce commutateur requiert l’argument /booklist ou l’argument /sourceURI.  Si vous spécifiez l’argument /sourceURI, tous les livres sont supprimés, et l’argument /booklist est ignoré.<br />-   **Move** : déplace le magasin local vers le chemin que vous spécifiez. Le chemin d’accès au magasin local par défaut est défini lors de la configuration de l’aide sous %PROGRAMDATA%.<br />     Ce commutateur requiert les arguments /locationPath et /catalogName. Les messages d’erreur sont collectés dans le journal des événements si vous spécifiez un chemin non valide ou si le lecteur ne contient pas suffisamment d’espace libre pour accueillir le contenu.<br />-   **Refresh** : met à jour les rubriques qui ont été modifiées depuis leur installation ou récemment mises à jour.<br />     Ce commutateur requiert l’argument /sourceURI.|  
|/catalogName|Oui|Spécifie le nom du catalogue de contenu.|  
|/locale|Non|Spécifie les paramètres régionaux du produit utilisés pour afficher et gérer le contenu pour l’instance actuelle de la visionneuse d’aide. Par exemple, vous spécifiez `EN-US` pour Anglais (États-Unis).<br /><br /> Si vous ne spécifiez pas de paramètres régionaux, ceux du système d’exploitation sont utilisés. S’ils ne peuvent pas être déterminés, `EN-US` est utilisé.<br /><br /> Si vous spécifiez des paramètres régionaux non valides, un message d’erreur est collecté dans le journal des événements.|  
|/e|Non|Élève le gestionnaire de contenu d’aide aux privilèges d’administrateur si l’utilisateur actuel dispose d’informations d’identification d’administration.|  
|/sourceURI|Non|Spécifie l’URL dont le contenu est installé (API de service) ou le chemin d’accès au fichier d’installation de contenu (.msha). L’URL peut pointer vers le groupe de produits (nœud de niveau supérieur) ou les livres de produit (nœud de niveau document) dans un point de terminaison de style Visual Studio 2010. Il n’est pas nécessaire d’inclure une barre oblique (/) à la fin de l’URL. Si vous le faites tout de même, elle est gérée correctement.<br /><br /> Un message d’erreur est collecté dans le journal des événements si vous spécifiez un fichier qui est introuvable, non valide, ou inaccessible, ou si une connexion à Internet n’est pas disponible ou est interrompue pendant la gestion du contenu.|  
|/vendor|Non|Spécifie le constructeur pour le contenu du produit qui sera supprimé (par exemple, `Microsoft`). L’argument par défaut pour ce commutateur est Microsoft.|  
|/productName|Non|Spécifie le nom du produit pour les livres qui seront supprimés. Le nom du produit est identifié dans les fichiers helpcontentsetup.msha ou books.html qui accompagnent le contenu. Vous pouvez supprimer des livres d’un seul produit à la fois. Pour supprimer des livres de plusieurs produits, vous devez exécuter plusieurs installations.|  
|/booklist|Non|Spécifie les noms des livres à gérer, séparés par des espaces. Les valeurs doivent correspondre aux noms de livres indiqués sur le support d’installation.<br /><br /> Si vous ne spécifiez pas cet argument, tous les livres recommandés pour le produit spécifié dans /sourceURI sont installés si la source d’installation est au format [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].<br /><br /> Si le nom d’un livre contient un ou plusieurs espaces, encadrez-le de guillemets doubles (") afin que la liste soit délimitée correctement.<br /><br /> Les messages d’erreur sont stockés si vous spécifiez un argument /sourceURI non valide ou inaccessible.|  
|/skuId|Non|Spécifie la référence SKU du produit depuis la source d’installation, puis filtre les livres que le commutateur /SourceURI identifie.|  
|/membership|Non|-   **Minimum** : installe un ensemble minimum de contenu d’aide sur la référence que vous spécifiez à l’aide du commutateur /skuId. Le mappage entre le SKU et l’ensemble de contenu est exposé dans l’API de service.<br />-   **Recommended** : installe un ensemble de livres recommandés pour la référence que vous spécifiez à l’aide de l’argument /skuId. La source d’installation est l’API de service ou le .MSHA.<br />-   **Full** : installe le jeu complet de livres pour la référence que vous spécifiez à l’aide de l’argument /skuId. La source d’installation est l’API de service ou le .MSHA.|  
|/locationpath|Non|Spécifie le dossier par défaut du contenu d’aide locale. Vous devez utiliser ce commutateur uniquement pour installer ou déplacer le contenu. Si vous spécifiez ce commutateur, vous devez également spécifier le commutateur /silent.|  
|/silent|Non|Installe ou supprime le contenu d’aide sans questionner l’utilisateur ou afficher d’élément d’interface utilisateur tel que l’icône dans la zone de notification d’état. La sortie est stockée dans un fichier dans le répertoire %Temp%. **Important :** Pour installer le contenu en mode silencieux, vous devez utiliser les fichiers signés numériquement .cab, pas les fichiers .mshc.|  
|/launchingApp|Non|Définit l’application et le contexte de catalogue lorsque la visionneuse d’aide est lancée sans application parente. Les arguments pour ce commutateur sont *CompanyName*, *ProductName* et *VersionNumber* (par exemple, `/launchingApp Microsoft,VisualStudio,11.0`).<br /><br /> Cet argument est requis pour installer le contenu avec le paramètre /silent.|  
|/wait *secondes*|Non|Suspend les opérations d’installation, de désinstallation et d’actualisation. Si une opération est en cours pour le catalogue, le processus attend jusqu’au nombre donné de secondes pour continuer. Utilisez 0 pour une attente indéfinie.|  
|/?|Non|Répertorie les commutateurs, ainsi que leur description, de l’outil en ligne de commande pour le gestionnaire de contenu d’aide.|  
  
### <a name="exit-codes"></a>Codes de sortie  
 Lorsque vous exécutez l’outil en ligne de commande pour le gestionnaire de contenu d’aide en mode silencieux, il renvoie les codes de sortie suivants :  
  
```  
Success = 0,  
  
FailureToElevate = 100  
InvalidCmdArgs = 101,  
FailOnFetchingOnlineContent = 110,  
FailOnFetchingContentFromDisk = 120,  
FailOnFetchingInstalledBooks = 130,  
NoBooksToUninstall = 200,  
NoBooksToInstall = 300,  
FailOnUninstall = 400,  
FailOnInstall = 500,  
FailOnMove = 600,  
FailOnUpdate = 700,  
FailOnRefresh = 800,  
Cancelled = 900,  
Others = 999,  
ContentManagementDisabled = 1200,  
OnlineHelpPreferenceDisabled = 1201  
UpdateAlreadyRunning = 1300 - (Signals that the update didn't run because another was in progress.)  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de l’administrateur Help Viewer](../ide/help-viewer-administrator-guide.md)   
 [Substitutions Help Content Manager](../ide/help-content-manager-overrides.md)
