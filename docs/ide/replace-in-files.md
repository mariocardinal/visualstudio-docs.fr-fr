---
title: "Remplacer dans les fichiers | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- Find and Replace window, Replace in Files tab
- Replace in Files tab, Find and Replace window
ms.assetid: ca361466-53bd-44db-a28a-3a74bc03b028
caps.latest.revision: 29
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
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 79206d09446dcd76654c3c24976fab3fe65e4f83
ms.contentlocale: fr-fr
ms.lasthandoff: 05/24/2017

---
# <a name="replace-in-files"></a>Remplacer dans les fichiers
**Remplacer dans les fichiers** vous permet de rechercher une chaîne ou une expression dans le code d’un ensemble défini de fichiers, et de modifier l’ensemble ou une partie des correspondances trouvées. Les correspondances trouvées et les actions entreprises sont répertoriées dans la fenêtre **Résultats de la recherche** sélectionnée dans **Options de résultat**.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Vous pouvez utiliser l’une des méthodes suivantes pour afficher l’option **Remplacer dans les fichiers** dans la fenêtre **Rechercher et remplacer**.  
  
### <a name="to-display-replace-in-files"></a>Pour afficher Remplacer dans les fichiers  
  
1.  Dans le menu **Edition**, développez **Rechercher et remplacer**.  
  
2.  Choisissez **Remplacer dans les fichiers**.  
  
     — ou —  
  
     Si la fenêtre **Rechercher et remplacer** est déjà ouverte, dans la barre d’outils, choisissez **Remplacer dans les fichiers**.  
  
## <a name="find-what"></a>Rechercher  
 Pour rechercher une nouvelle chaîne de texte ou expression, entrez-la dans cette zone. Pour rechercher une des 20 dernières chaînes que vous avez recherchées récemment, ouvrez la liste et sélectionnez la chaîne à rechercher. Choisissez le bouton adjacent **Générateur d’expressions** si vous souhaitez utiliser une ou plusieurs expressions régulières dans votre chaîne de recherche. Pour plus d’informations, consultez [Utilisation d’expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## <a name="replace-with"></a>Remplacer par  
 Pour remplacer des instances de la chaîne dans la zone **Rechercher** par une autre chaîne, entrez la chaîne de remplacement dans la zone **Remplacer par**. Pour supprimer des instances de la chaîne dans la zone **Rechercher**, laissez ce champ vide. Ouvrez la liste pour afficher les 20 chaînes que vous avez recherchées le plus récemment. Choisissez le bouton adjacent **Générateur d’expressions** si vous souhaitez utiliser une ou plusieurs expressions régulières dans votre chaîne de remplacement. Pour plus d’informations, consultez [Utilisation d’expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## <a name="look-in"></a>Regarder dans  
 L’option choisie dans la liste déroulante **Regarder dans** détermine si l’opération **Remplacer dans les fichiers** porte sur les fichiers actifs uniquement ou sur tous les fichiers figurant dans certains dossiers. Sélectionnez une étendue de recherche dans la liste, tapez le chemin d’un dossier ou cliquez sur le bouton **Parcourir (...)** pour afficher la boîte de dialogue **Choisir des dossiers de recherche** et choisissez un ensemble de dossiers. Vous pouvez également taper un chemin directement dans la zone **Regarder dans**.  
  
> [!NOTE]
>  Si l’option **Regarder dans** sélectionnée entraîne la recherche dans un fichier que vous avez extrait du contrôle de code source, la recherche ne porte que sur la version du fichier ayant été téléchargée sur votre ordinateur local.  
  
## <a name="find-options"></a>Options de recherche  
 Vous pouvez développer ou réduire la section **Options de recherche**. Les options suivantes peuvent être sélectionnées ou désélectionnées :  
  
 Respecter la casse  
 Quand vous sélectionnez cette option, les fenêtres **Résultats de la recherche** afficheront seulement les instances de la chaîne **Rechercher** dont le contenu et la casse sont identiques. Par exemple, la recherche de « MyObject » avec l’option **Respecter la casse** sélectionnée retourne « MyObject », mais pas « myobject » ni « MYOBJECT ».  
  
 Mot entier  
 Quand vous sélectionnez cette option, les fenêtres **Résultats de la recherche** afficheront seulement les instances de la chaîne **Rechercher** contenant les mêmes mots entiers. Par exemple, la recherche de « MyObject » retourne « MyObject », mais pas « CMyObject » ni « MyObjectC ».  
  
 Utiliser des expressions régulières  
 Quand cette case est cochée, vous pouvez utiliser des notations spéciales pour définir des modèles de texte dans les zones de texte **Rechercher** ou **Remplacer par**. Pour obtenir la liste de ces notations, consultez [Utilisation d’expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 Examiner ces types de fichiers  
 Cette liste indique les types de fichiers à examiner dans les répertoires choisis dans **Regarder dans**. Si ce champ est laissé vide, tous les fichiers dans les répertoires choisis dans **Regarder dans** sont examinés.  
  
 Sélectionnez un élément dans la liste pour entrer une chaîne de recherche prédéfinie à rechercher dans les fichiers de ces types particuliers.  
  
## <a name="result-options"></a>Options de résultat  
 Vous pouvez développer ou réduire la section **Options de résultat**. Les options suivantes peuvent être sélectionnées ou désélectionnées :  
  
 Fenêtre Résultats de la recherche 1  
 Si cette option est sélectionnée, les résultats de la recherche actuelle remplacent le contenu de la fenêtre **Résultats de la recherche 1**. Cette fenêtre s'ouvre automatiquement pour afficher les résultats de votre recherche. Pour ouvrir cette fenêtre manuellement, sélectionnez **Autres fenêtres** dans le menu **Affichage** et choisissez **Résultats de la recherche 1**.  
  
 Fenêtre Résultats de la recherche 2  
 Si cette option est sélectionnée, les résultats de la recherche actuelle remplacent le contenu de la fenêtre **Résultats de la recherche 2**. Cette fenêtre s'ouvre automatiquement pour afficher les résultats de votre recherche. Pour ouvrir cette fenêtre manuellement, sélectionnez **Autres fenêtres** dans le menu **Affichage** et choisissez **Résultats de la recherche 2**.  
  
 Afficher uniquement les noms de fichier  
 Quand cette case est cochée, les fenêtres Résultats de la recherche listent les noms complets et les chemins de tous les fichiers qui contiennent la chaîne de recherche. Toutefois, les résultats ne contiennent pas la ligne de code où apparaît la chaîne. Cette case à cocher n’est disponible que pour Rechercher dans les fichiers.  
  
 Conserver fich. modifiés ouverts après remplacement global  
 Quand cette option est sélectionnée, tous les fichiers dans lesquels des remplacements ont été effectués restent ouverts et vous pouvez ainsi annuler ou enregistrer les modifications. Les contraintes de mémoire peuvent limiter le nombre de fichiers qui peuvent rester ouverts suite à une opération de remplacement.  
  
> [!CAUTION]
>  Vous pouvez utiliser **Annuler** uniquement sur les fichiers qui restent ouverts pour modification. Si cette option n’est pas sélectionnée, les fichiers qui n’étaient pas déjà ouverts pour modification restent fermés, et aucune option **Annuler** n’est disponible dans ces fichiers.  
  
## <a name="see-also"></a>Voir aussi  
 [Recherche et remplacement de texte](../ide/finding-and-replacing-text.md)   
 [Rechercher dans les fichiers](../ide/find-in-files.md)   
 [Commandes Visual Studio](../ide/reference/visual-studio-commands.md)
