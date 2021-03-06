---
title: "Comment : utiliser des extraits de code XML | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d442dbf376d5615b6c10842c16d01183fc70056a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-xml-snippets"></a>Procédure : utiliser des extraits XML
Vous pouvez invoquer des extraits XML en utilisant les deux commandes suivantes du menu contextuel de l'éditeur XML. Le **insérer un extrait** commande insère l’extrait XML à la position du curseur. Le **entourer** commande encapsule l’extrait XML autour du texte sélectionné. Chaque extrait XML possède des types d'extrait désignés. Le type d’extrait détermine si l’extrait de code est disponible avec le **insérer un extrait** commande, le **entourer** commande, ou les deux.  
  
 Une fois l'extrait XML ajouté à l'éditeur, tous ses champs modifiables sont surlignés en jaune et le curseur est placé dans le premier d'entre eux.  
  
## <a name="insert-snippet"></a>Insérer un extrait  
 Les procédures suivantes décrivent comment accéder à la **insérer un extrait** commande.  
  
> [!NOTE]
>  Le **insérer un extrait** commande est également disponible via un raccourci clavier (CTRL + K, puis CTRL + X).  
  
#### <a name="to-insert-snippets-from-the-shortcut-menu"></a>Pour insérer des extraits à partir du menu contextuel  
  
1.  Placez le curseur à l'endroit où vous souhaitez insérer l'extrait XML.  
  
2.  Avec le bouton droit et sélectionnez **insérer un extrait**.  
  
     Une liste des extraits XML disponibles s'affiche.  
  
3.  Sélectionnez un extrait dans la liste à l'aide de la souris ou en entrant son nom et en appuyant sur TAB ou ENTRÉE.  
  
#### <a name="to-insert-snippets-using-the-intellisense-menu"></a>Pour insérer des extraits à l'aide du menu IntelliSense  
  
1.  Placez le curseur à l'endroit où vous souhaitez insérer l'extrait XML.  
  
2.  À partir de la **modifier** menu, pointez sur **IntelliSense**, puis sélectionnez **insérer un extrait**.  
  
     Une liste des extraits XML disponibles s'affiche.  
  
3.  Sélectionnez un extrait dans la liste à l'aide de la souris ou en entrant son nom et en appuyant sur TAB ou ENTRÉE.  
  
#### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>Pour insérer des extraits via la liste de remplissage IntelliSense  
  
1.  Placez le curseur à l'endroit où vous souhaitez insérer l'extrait XML.  
  
2.  Commencez à entrer l'extrait XML à ajouter à votre fichier. Si le remplissage automatique est activé, la liste de remplissage IntelliSense s'affiche. Dans le cas contraire, appuyez sur CTRL+ESPACE pour l'activer.  
  
3.  Sélectionnez l'extrait XML dans la liste de remplissage.  
  
4.  Appuyez sur TAB à deux reprises pour invoquer l'extrait XML.  
  
> [!NOTE]
>  Parfois, l'extrait XML n'est pas invoqué. Par exemple, si vous tentez d'insérer un élément `xs:complexType` dans un nœud `xs:element`, l'éditeur ne génère aucun extrait XML. En effet, lorsqu'un élément `xs:complexType` est utilisé à l'intérieur d'un nœud `xs:element`, aucun attribut ni sous-élément n'est requis, de sorte que l'éditeur n'a aucune donnée à insérer.  
  
#### <a name="to-insert-snippets-using-the-shortcut-name"></a>Pour insérer des extraits à l'aide du nom raccourci  
  
1.  Placez le curseur à l'endroit où vous souhaitez insérer l'extrait XML.  
  
2.  Entrez `<` dans le volet de l'éditeur.  
  
3.  Appuyez sur ÉCHAP pour fermer la liste de remplissage IntelliSense.  
  
4.  Entrez le nom raccourci de l'extrait XML, puis appuyez sur TAB pour l'invoquer.  
  
## <a name="surround-with"></a>Entourer de  
 Les procédures suivantes décrivent comment accéder à la **entourer** commande.  
  
> [!NOTE]
>  Le **entourer** commande est également disponible via un raccourci clavier (CTRL + K, puis CTRL + S).  
  
#### <a name="to-use-surround-with-from-the-context-menu"></a>Pour utiliser la commande Entourer de du menu contextuel  
  
1.  Sélectionnez le texte à entourer dans l'éditeur XML.  
  
2.  Avec le bouton droit et sélectionnez **entourer**.  
  
     Une liste des encadrements d'extraits XML disponibles s'affiche.  
  
3.  Sélectionnez un extrait dans la liste à l'aide de la souris ou en entrant son nom et en appuyant sur TAB ou ENTRÉE.  
  
#### <a name="to-use-surround-with-from-the-intellisense-menu"></a>Pour utiliser un encadrement à partir du menu Intellisense  
  
1.  Sélectionnez le texte à entourer dans l'éditeur XML.  
  
2.  À partir de la **modifier** menu, pointez sur **IntelliSense**, puis sélectionnez **entourer**.  
  
     Une liste des encadrements d'extraits XML disponibles s'affiche.  
  
3.  Sélectionnez un extrait dans la liste à l'aide de la souris ou en entrant son nom et en appuyant sur TAB ou ENTRÉE.  
  
## <a name="using-xml-snippets"></a>Utilisation d'extraits XML  
 Une fois que vous avez choisi un extrait XML, le texte de cet extrait de code est automatiquement inséré à l'emplacement du curseur. Tous les champs modifiables contenus dans l'extrait sont surlignés et le premier de ces champs est automatiquement sélectionné. Le champ actuellement sélectionné est encadré.  
  
 Après avoir sélectionné un champ, vous pouvez y entrer une nouvelle valeur. La touche TAB permet de parcourir en boucle les champs modifiables de l'extrait ; les touches MAJ+TAB effectuent le même parcours dans l'ordre inverse. Cliquer dans un champ place le curseur dans ce champ ; double-cliquer sur un champ permet de le sélectionner. Lorsqu'un champ est en évidence, une info-bulle peut s'afficher pour le décrire.  
  
 Seule la première instance d'un champ donné est modifiable. Lorsque ce champ est surligné, les autres instances du même champ sont mises en évidence. Lorsque vous modifiez la valeur d'un champ modifiable, ce champ change partout où il est utilisé dans l'extrait.  
  
 Appuyez sur ENTRÉE ou sur ÉCHAP pour annuler la modification du champ et revenir au mode normal de l'éditeur.  
  
 Les couleurs par défaut pour les champs d’extrait de code modifiable peuvent être modifiées en modifiant le paramètre du champ extrait de Code dans le **polices et couleurs** volet de la **Option**boîte de dialogue. Pour plus d’informations, consultez [Comment : modifier les polices et couleurs dans l’éditeur](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Extraits XML](../xml-tools/xml-snippets.md)   
 [Comment : générer un extrait XML à partir d’un schéma XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)   
 [Guide pratique pour créer des extraits XML](../xml-tools/how-to-create-xml-snippets.md)