---
title: "D&#233;finition de formes et de connecteurs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1fae548d-9288-4dd5-a24f-ff0d69c73628
caps.latest.revision: 3
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 3
---
# D&#233;finition de formes et de connecteurs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il existe plusieurs types élémentaires de formes que vous pouvez utiliser pour afficher les informations sur le diagramme d'un langage spécifique à un domaine \(DSL\).  
  
##  <a name="shapeTypes"></a> Types élémentaires de formes et de connecteurs  
 Un diagramme DSL affiche une collection de *formes* reliées par des lignes ou *connecteurs*.  En règle générale, sans que ce soit systématique :  
  
-   Les formes sont la représentation visible d'éléments de modèle.  
  
-   Les connecteurs représentent les relations de référence.  
  
-   Le diagramme représente l'instance racine du modèle.  
  
-   Les relations d'incorporation entre éléments de modèle sont affichées par contenance.  Par exemple, les éléments représentant les ports d'un composant sont incorporés au composant.  
  
 Ces modèles ne sont pas appliqués, mais sont pris en charge plus fortement.  Lors de la conception d'un DSL, gardez à l'esprit que la conception des relations d'incorporation doit être influencée par la façon dont vous voulez présenter le modèle sur l'écran.  Par contraste, les relations de référence doivent refléter les concepts de votre domaine d'activité.  
  
 Les types de formes suivants sont disponibles :  
  
|Type de forme|Description|  
|-------------------|-----------------|  
|Forme géométrique|Forme rectangulaire ou elliptique à caractère général.  Vous pouvez afficher les décorateurs de texte et d'icône à des positions spécifiques par rapports aux limites de la forme.<br /><br /> Pour imbriquer des formes à l'intérieur des formes géométriques, consultez [Imbrication de formes](../modeling/nesting-shapes.md).|  
|Forme de compartiment|Rectangle contenant un en\-tête et des compartiments, comme une classe UML.  Chaque compartiment peut contenir une liste de lignes de texte.<br /><br /> Les lignes représentent généralement les éléments incorporés sous l'élément représenté par la forme.  À titre d'exemple, créez un DSL à partir du modèle de solution Diagrammes de classes.|  
|Forme image|Forme qui affiche une image.|  
|Forme port|Petit rectangle destiné à être attaché au contour d'une autre forme.  Généralement utilisé dans les modèles de composants.<br /><br /> L'élément de modèle représenté par un port est généralement incorporé sous l'élément représenté par la forme parente.  À titre d'exemple, créez un DSL à partir du modèle de solution Composants.<br /><br /> Par défaut, une forme port peut glisser le long des côtés de sa forme parente.  Vous pouvez définir une règle des limites pour la contraindre à un emplacement particulier.<br /><br /> En rendant une forme port très petite et transparente, vous pouvez l'utiliser pour fournir un point de connexion fixe sur la surface de sa forme parente.|  
|Couloirs|Les couloirs partitionnent un diagramme en segments horizontaux ou verticaux.  Le couloir demeure toujours sous les autres formes du diagramme.<br /><br /> Généralement, les éléments de modèle du couloir sont apparentés à la racine du modèle et les autres éléments leur sont apparentés à leur tour.  À titre d'exemple, créez un DSL à partir du modèle de solution Flux de tâches.|  
|Connecteurs|Les lignes tracées entre les formes représentent généralement les relations de référence.  Vous pouvez définir des options pour rendre un connecteur droit ou rectiligne, ainsi que pour obtenir différents types de flèche.|  
  
##  <a name="shapeInheritance"></a> Héritage de forme  
 Une forme peut hériter d'une autre forme.  Cependant, les formes doivent être du même type.  Par exemple, seule une forme géométrique peut hériter d'une forme géométrique.  Les formes héritées possèdent les compartiments et décorateurs de leur forme de base.  Les connecteurs peuvent hériter de connecteurs.