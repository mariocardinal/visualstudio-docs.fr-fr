---
title: "Synchroniser vos paramètres dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/23/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: 10
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
translationtype: Human Translation
ms.sourcegitcommit: 4166ed8bfa0234e1cc453bd045974b412f87ae42
ms.openlocfilehash: a1a310aa6bf0e3d0042f35f5c49612f33b89fb61
ms.lasthandoff: 02/22/2017

---
# <a name="synchronize-your-settings-in-visual-studio"></a>Synchroniser vos paramètres dans Visual Studio
Quand vous vous connectez à Visual Studio sur plusieurs ordinateurs en utilisant le même compte de personnalisation, vos paramètres sont synchronisés par défaut sur tous les ordinateurs.

## <a name="synchronized-settings"></a>Paramètres synchronisés  
 Par défaut, les paramètres suivants sont synchronisés.  

-   Paramètres de développement (vous devez sélectionner un ensemble de paramètres la première fois que vous exécutez Visual Studio, mais vous pouvez modifier la sélection à tout moment. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).)  

-   Les options suivantes des pages **Outils &#124; Options** :  

    -   Paramètres **Thème** et paramètres de mise en majuscules de la barre de menus, dans la page d’options **Environnement**, **Général**  

    -   Tous les paramètres de la page d’options **Environnement**, **Polices et couleurs**  

    -   Tous les raccourcis clavier de la page d’options **Environnement**, **Clavier**  

    -   Tous les paramètres de la page d’options **Environnement, onglets et fenêtres**  

    -   Tous les paramètres de la page d’options **Environnement**, **Démarrage**  

    -   Tous les paramètres des pages d’options de l’**éditeur de texte**  

-   Tous les paramètres sur les pages d'options du concepteur XAML  

-   Alias de commande définis par l'utilisateur. Pour plus d’informations sur la façon de définir des alias de commande, consultez [Alias de commandes Visual Studio](../ide/reference/visual-studio-command-aliases.md).  

-   Dispositions des fenêtres définies par l’utilisateur dans la page **Fenêtre &#124; Gérer les dispositions de fenêtres**  

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Désactiver les paramètres synchronisés sur un ordinateur particulier  
 Les paramètres synchronisés pour Visual Studio sont activés par défaut. Vous pouvez désactiver les paramètres synchronisés sur un ordinateur en accédant à la page **Outils &#124; Options &#124; Environnement &#124; Paramètres synchronisés**, puis en décochant la case correspondante.  Par exemple, si vous décidez de ne pas synchroniser les paramètres de Visual Studio sur l’ordinateur A, toutes les modifications de paramètres effectuées sur l’ordinateur A n’apparaissent pas sur l’ordinateur B ou sur l’ordinateur C. Les ordinateurs B et C continuent à se synchroniser entre eux, mais pas avec l’ordinateur A.  

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Synchroniser les paramètres entre les éditions et les produits de la famille Visual Studio  
 Les paramètres peuvent être synchronisés entre toutes les éditions de Visual Studio, dont Community Edition. Les paramètres sont également synchronisés entre les produits de la famille Visual Studio. Toutefois, chacun de ces produits de la famille peut avoir ses propres paramètres qui ne sont pas partagés avec Visual Studio. Par exemple, les paramètres spécifiques à un produit sur l’ordinateur A seront partagés avec un autre produit sur l’ordinateur B, mais pas avec Visual Studio sur l’ordinateur A ou B.  

## <a name="see-also"></a>Voir aussi  
 [Personnalisation de l’IDE](../ide/personalizing-the-visual-studio-ide.md)
