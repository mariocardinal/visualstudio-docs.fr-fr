---
title: "Élément de bitmap | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 223342709dbe97fe38fb7a495ce482ae70e1c807
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="bitmap-element"></a>Élément de bitmap
Définit une image bitmap. La bitmap est chargée à partir d’une ressource ou d’un fichier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|GUID|Obligatoire. GUID de l’identificateur de commande/ID GUID.<br /><br /> L’attribut de guid pour une image bitmap n’est pas associé à un VSPackage ou un autre groupe de commandes.  Il doit être unique pour la définition de bitmap et ne doit pas être utilisé à d’autres fins.|  
|ResID|ID de l’identificateur de commande/ID GUID. Le resID ou l’attribut href est requis.<br /><br /> L’attribut resID est un ID de ressource d’entier qui détermine la bande de bitmap qui doit être chargé lors de la fusion de table de commandes.  Lors du chargement de la table de commande en cours, les bitmaps spécifiées par l’ID de ressource est chargés à partir de la ressource du même module.|  
|usedList|Obligatoire si l’attribut resID est présent. Sélectionne les images disponibles dans la bande de la bitmap.|  
|href|Chemin d’accès à l’image bitmap. Le resID ou l’attribut href est requis.<br /><br /> Le chemin d’accès include est recherché dans le fichier image indiqué, qui est incorporé dans le fichier binaire qui en résulte.  Lors de la fusion de table de commande, l’image est copiée et aucune recherche de ressources supplémentaires ou de la charge n’est requis.  Si l’attribut usedList n’est pas présent, toutes les images dans la bande sont disponibles. **Remarque :** Images peuvent être fournies dans un des formats qui incluent .gif, .png et .bmp.  Les versions antérieures du compilateur ne prenait pas en charge les images bitmap 32 bits qui avait des informations alpha pour la transparence partielle. La solution de contournement pour ces versions est d’utiliser le format .png.|  
|Condition|Facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément Bitmaps](../extensibility/bitmaps-element.md)|Regroupe les éléments d’image Bitmap.|  
  
## <a name="example"></a>Exemple  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)