---
title: "Acc&#232;s aux donn&#233;es locales et distantes dans les applications ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Déploiement, données ClickOnce"
  - "accès aux données, applications ClickOnce"
ms.assetid: be5cbe12-6cb6-49c9-aa59-a1624e1eef3d
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Acc&#232;s aux donn&#233;es locales et distantes dans les applications ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La plupart des applications consomment ou produisent des données.[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vous propose diverses options pour lire et écrire les données, à la fois localement et à distance.  
  
## Données locales  
 Avec [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vous pouvez charger et stocker des données localement à l'aide de l'une des méthodes suivantes :  
  
-   Répertoire de données [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]  
  
-   Stockage isolé  
  
-   Autres fichiers locaux  
  
### Répertoire de données ClickOnce  
 Chaque application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installée sur un ordinateur local possède un répertoire de données stocké dans le dossier Documents and Settings de l'utilisateur. Tous les fichiers inclus dans une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] et marqués en tant que fichiers de « données » sont copiés dans ce répertoire quand une application est installée. Les fichiers de données peuvent être associés à tout type de fichier, les plus fréquemment utilisés étant les fichiers texte, XML et les fichiers de base de données tels que les fichiers .mdb de Microsoft Access.  
  
 Le répertoire de données est destiné aux données gérées par l'application, c'est\-à\-dire les données que l'application stocke et gère explicitement. Tous les fichiers statiques qui ne sont pas des dépendances et ne sont pas marqués en tant que « données » dans le manifeste d'application résident plutôt dans le répertoire de l'application. Ce répertoire contient les fichiers exécutables \(.exe\) et les assemblys de l'application.  
  
> [!NOTE]
>  Quand une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est désinstallée, son répertoire de données est également supprimé. N'utilisez jamais le répertoire de données pour stocker les données gérées par l'utilisateur final, telles que les documents.  
  
#### Marquage des fichiers de données dans une distribution ClickOnce  
 Pour placer un fichier existant dans le répertoire de données, vous devez marquer le fichier existant en tant que fichier de données dans le fichier manifeste de votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Pour plus d'informations, consultez [How to: Include a Data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
#### Lecture et écriture dans le répertoire de données  
 La lecture dans le répertoire de données implique que votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] demande une autorisation d'accès en lecture. De la même façon, l'écriture dans le répertoire requiert une autorisation d'accès en écriture. Votre application reçoit automatiquement cette autorisation si elle est configurée pour s'exécuter avec un niveau de confiance totale. Pour plus d’informations sur l’élévation d’autorisations pour votre application à l’aide de l’élévation d’autorisations ou du déploiement d’applications approuvées, consultez [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md).  
  
> [!NOTE]
>  Si votre organisation n'utilise pas le déploiement d'applications approuvées et a désactivé l'élévation d'autorisations, la déclaration des autorisations échoue.  
  
 Une fois que votre application dispose de ces autorisations, elle peut accéder au répertoire de données en appelant des méthodes sur les classes dans le <xref:System.IO>. Vous pouvez obtenir le chemin d'accès au répertoire de données dans une application Windows Forms [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à l'aide de la propriété <xref:System.Deployment.Application.ApplicationDeployment.DataDirectory%2A> définie sur la propriété <xref:System.Deployment.Application.ApplicationDeployment.CurrentDeployment%2A> de <xref:System.Deployment.Application.ApplicationDeployment>. Il s'agit de la façon la plus pratique et recommandée pour accéder à vos données. L'exemple de code suivant montre comment procéder pour un fichier texte nommé CSV.txt que vous avez inclus dans votre déploiement en tant que fichier de données.  
  
 [!CODE [ClickOnce.OpenDataFile#1](../CodeSnippet/VS_Snippets_Winforms/ClickOnce.OpenDataFile#1)]  
  
 Pour plus d’informations sur le marquage des fichiers dans votre déploiement en tant que fichiers de données, consultez [How to: Include a Data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
 Vous pouvez également obtenir le chemin d'accès au répertoire de données en utilisant les variables appropriées sur la classe <xref:System.Windows.Forms.Application>, telles que <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A>.  
  
 La manipulation d'autres types de fichiers peut nécessiter des autorisations supplémentaires. Par exemple, si vous voulez utiliser un fichier de base de données Access \(.mdb\), votre application doit déclarer un niveau de confiance totale pour utiliser les classes <xref:System.Data> appropriées.  
  
#### Répertoire de données et versions d'application  
 Chaque version d'une application possède son propre répertoire de données, qui est isolé des autres versions.[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crée ce répertoire que des fichiers de données soient inclus ou non dans le déploiement, afin que l'application dispose d'un emplacement pour créer des fichiers de données au moment de l'exécution. Quand une nouvelle version d'une application est installée, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] copie tous les fichiers de données existants du répertoire de données de la version précédente dans le répertoire de données de la nouvelle version, qu'ils aient été inclus dans le déploiement d'origine ou créés par l'application.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] remplace l'ancienne version du fichier par la version la plus récente du serveur si un fichier de données a une valeur de hachage dans l'ancienne version de l'application différente de celle de la nouvelle version. En outre, si la version antérieure de l'application a créé un nouveau fichier de même nom qu'un fichier inclus dans le déploiement de la nouvelle version, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] remplace le fichier de l'ancienne version par le nouveau fichier. Dans les deux cas, les anciens fichiers sont inclus dans un sous\-répertoire du répertoire de données appelé `.pre`, de sorte que l’application peut toujours accéder aux anciennes données à des fins de migration.  
  
 Si vous avez besoin d'effectuer une migration de données plus précise, vous pouvez utiliser l'API de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pour effectuer une migration personnalisée de l'ancien répertoire de données vers le nouveau. Vous devrez vérifier qu'un téléchargement est disponible à l'aide de <xref:System.Deployment.Application.ApplicationDeployment.IsFirstRun%2A>, télécharger la mise à jour à l'aide de <xref:System.Deployment.Application.ApplicationDeployment.Update%2A> ou <xref:System.Deployment.Application.ApplicationDeployment.UpdateAsync%2A>, et effectuer manuellement toute tâche de migration de données personnalisée une fois la mise à jour terminée.  
  
### Stockage isolé  
 Le stockage isolé fournit une API pour la création et l'accès aux fichiers à l'aide d'une API simple. L'emplacement réel des fichiers stockés est masqué pour le développeur et l'utilisateur.  
  
 Le stockage isolé fonctionne dans toutes les versions du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Le stockage isolé fonctionne également dans les applications partiellement approuvées sans nécessité d'autorisations supplémentaires. Vous devez utiliser le stockage isolé si votre application doit s'exécuter en mode de confiance partielle, mais qu'elle doit conserver les données propres à l'application.  
  
 Pour plus d'informations, consultez [Stockage isolé](../Topic/Isolated%20Storage.md).  
  
### Autres fichiers locaux  
 Si votre application doit utiliser ou enregistrer des données de l'utilisateur final telles que des rapports, images, musique, etc., votre application a besoin de <xref:System.Security.Permissions.FileIOPermission> pour lire et écrire des données dans le système de fichiers local.  
  
## Données distantes  
 Dans certains cas, votre application devra probablement récupérer des informations à partir d'un site web distant, comme des données client ou des informations sur le marché. Cette section traite des techniques les plus courantes pour récupérer des données distantes.  
  
### Accès aux fichiers à l'aide de HTTP  
 Vous pouvez accéder aux données à partir d'un serveur web à l'aide de la classe <xref:System.Net.WebClient> ou <xref:System.Net.HttpWebRequest> dans l'espace de noms <xref:System.Net>. Les données peuvent être des fichiers statiques ou des applications [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] qui retournent du texte brut ou des données XML. Si vos données sont au format XML, le moyen le plus rapide de les récupérer est d'utiliser la classe <xref:System.Xml.XmlDocument>, dont la méthode <xref:System.Xml.XmlDocument.Load%2A> accepte une URL comme argument. Pour obtenir un exemple, consultez [Lecture d'un document XML dans le DOM](../Topic/Reading%20an%20XML%20Document%20into%20the%20DOM.md).  
  
 Vous devez prendre en compte la sécurité quand votre application accède à des données distantes sur HTTP. Par défaut, l'accès de votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aux ressources réseau peut être restreint, selon la façon dont votre application a été déployée. Ces restrictions sont appliquées pour empêcher les programmes malveillants d'accéder à des données distantes privilégiées ou d'utiliser l'ordinateur d'un utilisateur pour attaquer d'autres ordinateurs sur le réseau.  
  
 Le tableau suivant répertorie les stratégies de déploiement que vous pouvez utiliser ainsi que leurs autorisations web par défaut.  
  
|Type de déploiement|Autorisations réseau par défaut|  
|-------------------------|-------------------------------------|  
|Installation web|Ne peut accéder qu'au serveur web à partir duquel l'application a été installée.|  
|Installation à partir d'un partage de fichiers|Ne peut pas accéder à tous les serveurs web|  
|Installation à partir d'un CD\-ROM|Peut accéder à tous les serveurs web|  
  
 Si votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ne peut pas accéder à un serveur web en raison des restrictions de sécurité, l'application doit déclarer <xref:System.Net.WebPermission> pour ce site web. Pour plus d'informations sur l'augmentation des autorisations de sécurité pour une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], consultez [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md).  
  
### Accès aux données via un service web XML  
 Si vous exposez vos données en tant que service web XML, vous pouvez accéder aux données à l'aide d'un proxy de service web XML. Le proxy est une classe [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que vous créez à l'aide de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Les opérations du service web XML, par exemple, la récupération de clients, le passage de commandes, etc., sont exposées en tant que méthodes sur le proxy. De cette façon, les services web sont beaucoup plus faciles à utiliser que les fichiers de texte brut ou XML.  
  
 Si votre service web XML fonctionne sur HTTP, le service sera lié par les mêmes restrictions de sécurité que les classes <xref:System.Net.WebClient> et <xref:System.Net.HttpWebRequest>.  
  
### Accès direct à une base de données  
 Vous pouvez utiliser les classes de l'espace de noms <xref:System.Data> pour établir des connexions directes à un serveur de base de données tel que SQL Server sur votre réseau, mais vous devez prendre en compte les problèmes de sécurité. Contrairement aux requêtes HTTP, les demandes de connexion de base de données sont toujours interdites par défaut dans un contexte de confiance partielle. Vous n'obtenez cette autorisation par défaut que si vous installez votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à partir d'un CD\-ROM. Ce qui lui donne un niveau de confiance totale. Pour permettre l'accès à une base de données SQL Server spécifique, votre application doit lui demander l'autorisation <xref:System.Data.SqlClient.SqlClientPermission>, pour permettre l'accès à une base de données autre que SQL Server, elle doit demander l'autorisation <xref:System.Data.OleDb.OleDbPermission>.  
  
 La plupart du temps, vous n'aurez pas besoin d'accéder directement à la base de données, mais plutôt via une application de serveur web écrite en [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ou un service web XML. L'accès à la base de données de cette manière est généralement la meilleure méthode si votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est déployée à partir d'un serveur web. Vous pouvez accéder au serveur dans un contexte de confiance partielle sans élever les autorisations de votre application.  
  
## Voir aussi  
 [How to: Include a Data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)