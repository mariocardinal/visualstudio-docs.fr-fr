---
title: "DA0502 : Consommation CPU maximale par le processus en cours de profilage | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.rules.DA0502
- vs.performance.DA0502
- vs.performance.502
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d1cd5fbe91b125c00fe617f03711ea52cdf458f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="da0502-maximum-cpu-consumption-by-the-process-being-profiled"></a>DA0502 : Consommation CPU maximale par le processus en cours de profilage
|||  
|-|-|  
|ID de règle|DA0502|  
|Catégorie|Analyse des ressources|  
|Méthode de profilage|Tout|  
|Message|Règle uniquement pour informations. Le compteur Processus()\\% temps processus mesure la consommation CPU du processus que vous profilez. La valeur signalée correspond à la valeur maximale observée dans l’ensemble des intervalles de mesure.|  
|Type de règle|Informations|  
  
 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.  
  
## <a name="rule-description"></a>Description de la règle  
 Ce message indique le temps maximal, en pourcentage, pendant lequel un processeur a exécuté des instructions à partir de l’application. La valeur signalée correspond à la valeur maximale de tous les intervalles de mesure pendant lesquels le processus profilé était actif. Cette valeur peut être supérieure à 100 % sur les ordinateurs qui comprennent plusieurs processeurs.  
  
## <a name="how-to-use-the-rule-data"></a>Comment utiliser des données de règle  
 Utilisez la valeur de la règle pour comparer les performances des différentes versions du programme ou pour comprendre les performances de l’application dans différents scénarios de profilage.