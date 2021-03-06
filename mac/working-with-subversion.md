---
title: Utilisation de Subversion
description: Utilisation de Subversion dans Visual Studio pour Mac.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 2400ED9C-6236-4C0A-A3AB-9D7CBE1F0CF4
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 70cf7a411141c5a59e275cb455ddcf91863c4f8b
ms.contentlocale: fr-fr
ms.lasthandoff: 08/11/2017

---

# <a name="working-with-subversion"></a>Utilisation de Subversion

Comme mentionné précédemment dans cet article, Subversion est le système de gestion de version centralisé qui vous permet d’extraire une seule copie principale des données centralisées. Contrairement à Git, l’extraction d’un dépôt Subversion ne clone pas l’intégralité du dépôt, elle prend seulement une capture instantanée à ce point dans le temps.

Subversion utilise un modèle de type copier-modifier-fusionner pour permettre aux utilisateurs de travailler simultanément sur le même dépôt. Cela signifie que chaque utilisateur crée une copie locale, ou de travail, des données centralisées, sur laquelle ils peuvent travailler de manière indépendante. Les modifications apportées aux copies de travail des utilisateurs sont fusionnées de manière chronologique.

Par exemple, imaginez que l’utilisateur A et l’utilisateur B extraient tous deux une copie du dépôt distant et modifient les fichiers. L’utilisateur A termine les modifications et les valide à distance. Avant que l’utilisateur B valide son travail, il doit mettre à jour sa copie de travail avec les modifications de l’autre utilisateur, ce qui revient à fusionner les modifications de l’utilisateur A.

Dans les sections ci-dessous, nous allons examiner comment Subversion peut être utilisé pour la gestion de version dans Visual Studio pour Mac.

L’image ci-dessous illustre les options fournies par Visual Studio pour Mac par l’élément de menu Gestion de version :

![Éléments de menu Gestion de version](media/version-control-svnVersionControlMenu.png)

Les sections ci-dessous expliquent chaque option plus en détail.

## <a name="checkout"></a>Extraire...

Avant de commencer à utiliser un dépôt Subversion distant, vous devez extraire le dépôt pour créer une copie locale, ou de travail, de ce répertoire sur votre ordinateur local.

Pour en savoir sur l’utilisation de la fonctionnalité **Extraire** dans Visual Studio pour Mac, suivez les étapes de la section [Configuration d’un dépôt Subversion](~/set-up-subversion-repository.md).

## <a name="update-solution"></a>Mettre à jour la solution

Quand vous utilisez un dépôt distant, n’oubliez pas que les autres utilisateurs peuvent aussi modifier les fichiers et rendre votre copie de travail obsolète. Pour l’éviter, il est toujours recommandé de tirer (pull) toutes les modifications du dépôt dans votre solution avant de commencer à travailler et avant la validation. Pour ce faire, sélectionnez l’élément de menu *Gestion de version > Mettre à jour la solution*.

## <a name="review-solution-and-commit"></a>Examiner la solution et valider

Pour examiner les modifications apportées aux fichiers, utilisez les onglets Modifications, Responsable, Journal et Fusion de chaque document, comme illustré ci-dessous :

![Onglets de la gestion de version](media/version-control-vcTabs.png)

Examinez toutes les modifications d’un projet en accédant à l’élément de menu **Gestion de version > Examiner la solution et valider** :

![Examiner la solution](media/version-control-vcStatus.png)

Ce menu permet d’afficher toutes les modifications de chaque fichier d’un projet avec les options Restaurer, Créer un correctif ou Valider.

Pour valider un fichier dans le dépôt distant, appuyez sur Valider..., entrez un message de validation et confirmez avec le bouton Valider :


![Validation d’un fichier](media/version-control-svnCommit.png)

Cette action envoie les modifications dans le dépôt où elles constituent la nouvelle révision de toutes vos modifications.

