---
title: "Résolution des problèmes de déploiement de solutions Office | Documents Microsoft"
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
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- Office development in Visual Studio, troubleshooting
- deploying applications [Office development in Visual Studio], troubleshooting
ms.assetid: 2206aeb6-44b3-4786-ba99-9c7dad5cce7c
caps.latest.revision: "74"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 50df21e315aaaa9b0ecbc7d961fbc7b568646785
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="troubleshooting-office-solution-deployment"></a>Dépannage du déploiement de solutions Office
  Cette rubrique contient des informations sur la résolution des problèmes courants que vous pouvez rencontrer lorsque vous déployez des solutions Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="troubleshooting-office-solutions-by-using-the-event-viewer"></a>Résolution des problèmes liés aux solutions Office à l’aide de l’observateur d’événements  
 Vous pouvez utiliser l’observateur d’événements de Windows pour consulter les messages d’erreur capturés par [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] lors de l’installation ou de la désinstallation de solutions Office. Vous pouvez utiliser ces messages à partir du journal d’événements pour résoudre les problèmes d’installation et de déploiement. Pour plus d'informations, consultez [Event Logging for Office Solutions](../vsto/event-logging-for-office-solutions.md).  
  
## <a name="changing-the-assembly-name-causes-conflicts"></a>La modification du Nom de l’assembly provoque des conflits  
 Si vous modifiez le **nom de l’Assembly** valeur dans le **Application** page de la **Concepteur de projets** une fois que vous avez déjà déployé une solution, les outils de publication modifient le Package d’installation pour avoir un fichier Setup.exe et deux manifestes de déploiement. Si vous déployez deux fichiers manifeste, les conditions suivantes peuvent se produire :  
  
-   Si l’utilisateur final installe les deux versions, l’application charge les deux compléments VSTO.  
  
-   Si le complément VSTO a été installé avant que le nom de l’assembly ait été modifié, l’utilisateur final ne recevra jamais des mises à jour.  
  
 Pour éviter ces conditions, ne modifiez pas la solution **nom de l’Assembly** valeur après avoir déployé la solution.  
  
## <a name="checking-for-updates-takes-a-long-time"></a>La vérification des mises à jour prend beaucoup de temps  
 Visual Studio 2010 Tools pour Office Runtime fournit une entrée de Registre que les administrateurs peuvent utiliser pour définir la valeur du délai d’attente pour télécharger les manifestes et la solution.  
  
#### <a name="to-set-the-time-out-value"></a>Pour définir la valeur du délai d’attente  
  
1.  Dans le Registre, accédez à la clé suivante :  
  
     HKEY_CURRENT_USER\Software\Microsoft\VSTA  
  
2.  Dans la sous-clé **AddInTimeout** , définissez la valeur du délai d’attente en millisecondes.  
  
     Si la sous-clé **AddInTimeout** n’existe pas, créez-la comme valeur DWORD.  
  
## <a name="cant-update-or-publish-to-a-network-file-share"></a>Impossible d’effectuer une mise à jour ou de publier sur un partage de fichiers réseau  
 Les solutions Office qui se trouvent sur un partage de fichiers réseau peuvent afficher un message trompeur pendant les mises à jour si le fichier Setup.exe de la solution est verrouillé dans un processus pendant la publication de la mise à jour. Le message suivant peut s’afficher : « Impossible d’ajouter 'setup.exe' au site web. Le fichier 'setup.exe' existe déjà dans le site web. »  
  
 Pour empêcher le verrouillage du fichier, vous pouvez activer le partage en lecture seule pour les utilisateurs finaux. Toutefois, si les documents sont sur le partage, ils sont également activés en lecture seule pour les utilisateurs finaux.  
  
## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Les composants requis pour Microsoft Office ne sont pas installés  
 Vous pouvez ajouter le .NET Framework, la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]et les assemblys PIA (Primary Interop Assembly) Office à votre package d’installation comme composants requis déployés avec votre solution Office. Pour plus d’informations sur la façon d’installer les assemblys PIA, consultez [configuration d’un ordinateur pour développer des Solutions Office](../vsto/configuring-a-computer-to-develop-office-solutions.md) et [Comment : installer assemblys PIA Office](../vsto/how-to-install-office-primary-interop-assemblies.md).  
  
## <a name="publishing-using-localhost-can-cause-installation-problems"></a>La publication à l’aide de « localhost » peut provoquer des problèmes d’installation  
 Lorsque vous utilisez « http://localhost » comme emplacement de publication ou d’installation pour les solutions au niveau du document, l’ **Assistant Publication** ne convertit pas la chaîne en nom réel de l’ordinateur. Dans ce cas, la solution doit être installée sur l’ordinateur de développement. Pour que des solutions déployées utilisent IIS sur l’ordinateur de développement, utilisez le nom complet pour tous les emplacements HTTP/HTTPS/FTP au lieu de localhost.  
  
## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Les assemblys mis en cache sont chargés au lieu des assemblys mis à jour  
 Fusion, le chargeur d’assembly .Net Framework, charge la copie mise en cache des assemblys lorsque le chemin de sortie du projet est sur un partage de fichiers réseau, que l’assembly est signé avec un nom fort et que la version d’assembly de la personnalisation ne change pas. Si vous mettez à jour un assembly qui satisfait ces conditions, la mise à jour ne s’affiche pas lors de la prochaine exécution du projet, car la copie mise en cache est chargée.  
  
 Vous pouvez configurer Visual Studio pour que Fusion télécharge les assemblys chaque fois que le projet est exécuté.  
  
#### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>Pour télécharger des assemblys au lieu de charger des copies mises en cache  
  
1.  Dans la barre de menus, choisissez **Projet**, *Propriétés de***NomProjet**.  
  
2.  Dans la page **Application** , choisissez **Informations de l’assembly**.  
  
3.  Dans la première **Version de l’Assembly** , entrez un astérisque (\*), puis choisissez le **OK** bouton.  
  
 Après avoir modifié la version d’assembly, vous pouvez continuer à signer votre assembly avec un nom fort, et Fusion chargera la version de la personnalisation.  
  
## <a name="installation-fails-when-the-uri-has-characters-that-aret-us-ascii"></a>L’installation échoue lorsque l’URI comporte des caractères qui ne sont pas US-ASCII  
 Lorsque vous publiez une solution Office sur un emplacement HTTP/HTTPS/FTP, le chemin d’accès ne peut contenir aucun caractère Unicode qui ne sont pas en US-ASCII. Ces caractères peuvent provoquer un comportement anormal dans le programme d’installation. Utilisez des caractères US-ASCII pour le chemin d’installation.  
  
## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>L’invite de désinstallation manuelle s’affiche quand vous publiez et installez une solution sur l’ordinateur de développement  
 Lorsque vous générez une solution Office, la version créée est inscrite automatiquement. Si vous avez déjà publié et installé la même solution sur votre ordinateur de développement, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] détecte que le chemin d’installation de la version publiée et celui de la version générée sont différents après la génération, la régénération et la publication de l’application. Le message d’erreur suivant s’affiche : « La personnalisation ne peut pas être installée car une autre version est actuellement installée et ne peut pas être mis à niveau depuis cet emplacement. » Les clés de Registre sont mises à jour chaque fois qu’une solution est régénérée. Par conséquent, vous devez désinstaller la version précédente avant de publier, de déboguer ou d’exécuter la nouvelle version.  
  
 Pour empêcher l’affichage de ce message, créez un autre compte d’utilisateur sur votre ordinateur de développement pour tester votre déploiement. Vous pouvez également désinstaller la version de la liste des programmes installés sur l’ordinateur avant de publier, de déboguer ou de régénérer ensuite la solution.  
  
## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Exception non interceptée ou erreur de méthode introuvable lors de l’installation d’une solution  
 Lorsque vous installez des solutions Office en ouvrant le manifeste de déploiement (fichier .vsto), l’application Office, le document ou le classeur, des messages d’erreur relatifs aux conditions suivantes peuvent s’afficher :  
  
-   Méthode introuvable.  
  
-   MissingMethodException.  
  
-   Exception non interceptée.  
  
 Pour que ces messages d’erreur ne s’affichent pas, installez la solution en exécutant le programme d’installation.  
  
 Lorsque vous installez la solution sans exécuter le programme d’installation, celui-ci ne recherche pas ou n’installe pas les composants requis. Le programme d’installation vérifie si la version des composants requis est correcte et les installe si nécessaire.  
  
## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Les clés de Registre de manifeste pour les compléments changent après la génération d’un projet InstallShield Limited Edition  
 La clé de Registre de manifeste qui fait partie du programme d’installation d’un complément VSTO change parfois de .vsto à .dll.manifest lorsque vous générez un projet InstallShield Limited Edition.  
  
 Pour contourner ce problème, créez le projet InstallShield Limited Edition dans une autre solution ou utilisez CompanyName.AddinName comme valeur de la clé de Registre qui contient le nom du complément VSTO.  
  
## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Le programme d’installation ClickOnce de votre solution Office n’installe pas les assemblys PIA  
 Lorsque vous exécutez le programme d’installation que ClickOnce crée pour votre solution Office, le programme d’installation des assemblys PIA (Primary Interop Assemblies) Office s’exécute uniquement si aucun assembly PIA n’est déjà installé.  
  
 Si le programme d’installation n’installe pas les assemblys PIA correctement, installez-les manuellement en exécutant le fichier du programme d’installation nommé o2007pia.msi à partir du répertoire d’installation.  
  
## <a name="reinstalling-office-solutions-causes-an-argument-out-of-range-exception"></a>La réinstallation de solutions Office provoque une exception d’argument hors limites  
 Lorsque vous réinstallez une solution Office, une exception <xref:System.ArgumentOutOfRangeException> peut s’afficher avec le message d’erreur suivant : « L’argument spécifié n’était pas dans les limites de la plage des valeurs valides. »  
  
 Cette situation se produit si la casse de l’URL de l’emplacement d’installation est différente. Par exemple, cette erreur s’affiche si vous avez installé une solution Office à partir de [http://fabrikam.com/ExcelSolution.vsto](http://fabrikam.com/ExcelSolution.vsto) la première fois, puis que vous avez utilisé [http://fabrikam.com/excelsolution.vsto](http://fabrikam.com/excelsolution.vsto) la deuxième fois.  
  
 Pour empêcher l’affichage de ce message, utilisez la même casse lorsque vous installez des solutions Office.  
  
## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Impossible d’installer une solution ClickOnce en ouvrant le manifeste de déploiement à partir du web.  
 Les utilisateurs peuvent installer des solutions Office en ouvrant le manifeste de déploiement à partir du web. Toutefois, certaines installations des services IIS (Internet Information Services) bloquent l’extension de nom de fichier .vsto. Vous devez définir le type MIME dans IIS avant de l’utiliser pour déployer une solution Office.  
  
 Pour plus d’informations sur la façon de définir le type MIME dans IIS 6, consultez [Configurer les types MIME (IIS 6.0)](http://www.microsoft.com/technet/prodtechnol/WindowsServer2003/Library/IIS/cd72c0dc-c5b8-42e4-96c2-b3c656f99ead.mspx?mfr=true).  
  
 Pour plus d’informations sur la façon de définir le type MIME dans IIS 7, consultez [Ajouter un type MIME (IIS 7)](http://technet.microsoft.com/library/cc725608(WS.10).aspx).  
  
 Définissez l’extension sur **.vsto** et le type MIME sur **application/x-ms-vsto**.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des déploiements ClickOnce](/visualstudio/deployment/troubleshooting-clickonce-deployments)   
 [Déploiement d’une solution Office](../vsto/deploying-an-office-solution.md)  
  
  