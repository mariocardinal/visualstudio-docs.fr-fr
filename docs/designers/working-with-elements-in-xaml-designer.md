---
title: "Travailler avec des &#233;l&#233;ments dans le concepteur XAML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Travailler avec des &#233;l&#233;ments dans le concepteur XAML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez ajouter des éléments \(contrôles, dispositions et formes\) à votre application en XAML, dans le code ou à l'aide du concepteur XAML.  Cette rubrique décrit comment utiliser des éléments dans le concepteur XAML dans Visual Studio ou Blend pour Visual Studio.  
  
## Ajout d'un élément à une disposition  
 La *disposition* est le processus de dimensionnement et de positionnement des éléments dans une interface utilisateur.  Pour positionner des éléments visuels, vous devez les placer dans une [panneau](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.panel.aspx) de disposition.  Un `Panel` a une propriété enfant qui est une collection de types [FrameworkElement](http://msdn.microsoft.com/library/windows/apps/br208706.aspx).  Vous pouvez utiliser différents éléments enfants `Panel`, tels que [Canvas](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.canvas.aspx), [StackPanel](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.stackpanel.aspx) et [Grid](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx), en guise de conteneurs de disposition, ainsi que pour positionner et organiser les éléments d'une page.  
  
 Par défaut, un panneau `Grid` est utilisé comme conteneur de disposition de niveau supérieur dans un formulaire ou une page.  Vous pouvez ajouter des contrôles, des panneaux de disposition ou d'autres éléments dans la disposition de niveau supérieur.  
  
#### Pour ajouter un élément à une disposition  
  
-   Dans le concepteur XAML, effectuez l'une des opérations suivantes :  
  
    -   Double\-cliquez sur un élément dans la **boîte à outils** \(ou sélectionnez un élément dans la boîte à outils, et appuyez sur Entrée\).  
  
    -   Faites glisser un élément depuis la **boîte à outils** vers la planche graphique.  
  
    -   Dans la **boîte à outils**, sélectionnez un outil de dessin \(par exemple, [Ellipse](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.ellipse.aspx) ou [Rectangle](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.aspx)\), puis dessinez un élément dans le panneau actif.  
  
## Modification de l'ordre de superposition des éléments  
 Quand la planche graphique du concepteur XAML comporte deux éléments, l'un d'eux apparaît devant l'autre dans l'ordre de superposition.  Sauf si la propriété **ZIndex** d'un élément est définie, l'élément au premier plan se trouve en bas de la liste des éléments dans la fenêtre Structure du document.  Quand vous insérez un élément dans une page, un formulaire ou un conteneur de disposition, l'élément est automatiquement placé devant les autres éléments dans l'élément de conteneur actif.  Pour modifier l'ordre des éléments, vous pouvez utiliser les commandes **Ordre** ou faire glisser les éléments dans l'arborescence d'objets dans la fenêtre Structure du document.  
  
#### Pour modifier l'ordre de superposition  
  
-   Effectuez l’une des opérations suivantes :  
  
    -   Dans la fenêtre **Structure du document**, faites glisser les éléments vers le haut ou le bas pour créer l'ordre de superposition souhaité.  
  
    -   Dans la fenêtre Structure du document ou la planche graphique, cliquez avec le bouton droit sur l'élément pour lequel vous souhaitez modifier l'ordre de superposition, pointez sur **Ordre**, puis cliquez sur une des options suivantes :  
  
        -   **Mettre au premier plan** pour placer l'élément tout au début dans l'ordre.  
  
        -   **Avancer d'un plan** pour faire avancer l'élément d'un niveau dans l'ordre.  
  
        -   **Reculer d'un plan** pour faire reculer l'élément d'un niveau dans l'ordre.  
  
        -   **Mettre en arrière\-plan** pour placer l'élément tout à la fin dans l'ordre.  
  
     Modifiez la propriété **ZIndex** dans la section **Disposition** de la fenêtre Propriétés.  Dans le cas des éléments qui se chevauchent, la propriété **ZIndex** prévaut sur l'ordre des éléments affiché dans la fenêtre Structure du document.  Quand des éléments se chevauchent, l'élément qui possède une valeur **ZIndex** inférieure apparaît devant.  
  
## Modification de l'alignement d'un élément  
 Vous pouvez aligner des éléments dans la planche graphique à l'aide de commandes de menu ou en faisant glisser les éléments vers des lignes d'alignement.  
  
 Une *ligne d'alignement* est un repère visuel qui vous aide à aligner un élément par rapport à d'autres éléments dans l'application.  
  
#### Pour aligner deux ou plusieurs éléments à l'aide de commandes de menu  
  
1.  Sélectionnez les éléments que vous voulez aligner.  Pour sélectionner plusieurs éléments, appuyez sur la touche Ctrl, puis tout en la maintenant enfoncée, sélectionnez les éléments.  
  
2.  Sélectionnez une des propriétés suivantes sous **HorizontalAlignment** dans la section **Disposition** de la fenêtre Propriétés : **Gauche**, **Centre**, **Droite** ou **Étirer**.  
  
3.  Sélectionnez une des propriétés suivantes sous **VerticalAlignment** dans la section **Disposition** de la fenêtre Propriétés : **Haut**, **Centre**, **Bas** ou **Étirer**.  
  
#### Pour aligner deux ou plusieurs éléments à l'aide de lignes d'alignement  
  
-   Dans le concepteur XAML, dans une disposition qui contient au moins deux éléments, faites glisser ou redimensionnez l'un des éléments afin que le bord soit aligné sur un autre élément.  
  
     Quand les bords sont alignés, une *limite d'alignement* s'affiche pour indiquer l'alignement.  La limite d'alignement est une ligne en pointillés rouge.  Les limites d'alignement n'apparaissent que si l'**alignement sur les lignes d'alignement** est activé.  Pour une illustration de la planche graphique montrant une limite d'alignement, consultez [Création d'une interface utilisateur à l'aide du concepteur XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  
  
## Modification des marges d'un élément  
 Les marges dans le concepteur XAML déterminent la quantité d'espace vide autour d'un élément sur la planche graphique.  Par exemple, les marges spécifient la quantité d'espace entre les bords extérieurs d'un élément et les limites d'un panneau `Grid` qui contient cet élément.  Les marges spécifient également la quantité d'espace entre les éléments contenus dans un `StackPanel`.  
  
#### Pour modifier les marges d'un élément dans la fenêtre Propriétés  
  
1.  Sélectionnez l'élément dont vous souhaitez modifier les marges.  
  
2.  Sous **Disposition** dans la fenêtre Propriétés, modifiez la valeur \(en pixels ou en unités indépendantes du périphérique, qui représentent approximativement 1\/96e de pouce\) de toutes les propriétés **Marge** \(**Haut**, **Gauche**, **Droite** ou **Bas**\).  
  
#### Pour modifier les marges d'un élément dans la planche graphique  
  
-   Pour modifier les marges d'un élément par rapport à son conteneur de disposition, cliquez sur les *ornements de marge* ; ces derniers apparaissent autour de l'élément dans la planche graphique quand il est sélectionné et qu'il se trouve dans un conteneur de disposition.  Pour une illustration des ornements de marge, consultez [Création d'une interface utilisateur à l'aide du concepteur XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  
  
     Si un ornement de marge est ouvert, verticalement ou horizontalement, la marge correspondante n'est pas définie.  Par contre, s'il est fermé, la marge correspondante est définie.  
  
     Quand vous ouvrez un ornement de marge et que la marge opposée n'est pas définie, celle\-ci se voit attribuer une valeur appropriée en fonction de l'emplacement de l'élément dans la planche graphique.  Dans le cas des marges opposées, telles que les marges **Gauche** et **Droite**, au moins une propriété est toujours définie.  
  
    > [!IMPORTANT]
    >  Les éléments placés dans certains conteneurs de disposition, tels qu'un <xref:Windows.UI.Xaml.Controls.Canvas>, ne possèdent pas d'ornements de marge.  Les éléments placés dans un <xref:Windows.UI.Xaml.Controls.StackPanel> possèdent des ornements de marge pour les marges droite et gauche ou pour les marges supérieure et inférieure, selon l'orientation du `StackPanel`.  
  
## Regroupement et dissociation d'éléments  
 Le regroupement de deux ou plusieurs éléments dans le concepteur XAML crée un conteneur de disposition et y place ces éléments.  Placer deux ou plusieurs éléments ensemble dans un conteneur de disposition vous permet de facilement sélectionner, déplacer et transformer le groupe comme si les éléments de ce groupe constituaient un seul élément.  Le regroupement est également utile pour identifier les éléments qui ont un lien, tels que les boutons qui composent un élément de navigation.  Quand vous dissociez des éléments, vous supprimez simplement le conteneur de disposition qui les contenait.  
  
#### Pour regrouper des éléments dans un nouveau conteneur de disposition  
  
1.  Sélectionnez les éléments que vous voulez regrouper.  \(Pour sélectionner plusieurs éléments, appuyez sur la touche Ctrl puis, tout en la maintenant enfoncée, cliquez sur les éléments.\)  
  
2.  Cliquez avec le bouton droit sur les éléments sélectionnés, pointez sur **Grouper**, puis cliquez sur le type de conteneur de disposition dans lequel vous souhaitez que le groupe réside.  
  
    > [!TIP]
    >  Si vous sélectionnez <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> ou <xref:Windows.UI.Xaml.Controls.ScrollViewer> pour regrouper vos éléments, les éléments sont placés dans un nouveau panneau <xref:Windows.UI.Xaml.Controls.Grid> dans le <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> ou <xref:Windows.UI.Xaml.Controls.ScrollViewer>.  Si vous dissociez des éléments dans un de ces conteneurs de disposition, seuls le <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> ou <xref:Windows.UI.Xaml.Controls.ScrollViewer> est supprimé, tandis que le panneau <xref:Windows.UI.Xaml.Controls.Grid> reste.  Pour supprimer le panneau `Grid`, dissociez les éléments de nouveau.  
  
#### Pour dissocier des éléments et supprimer la disposition  
  
-   Cliquez avec le bouton droit sur le groupe à dissocier, puis cliquez sur **Dissocier**.  
  
 Vous pouvez également regrouper ou dissocier des éléments en cliquant avec le bouton droit sur les éléments concernés dans la fenêtre Structure du document, puis en cliquant sur **Grouper** ou **Dissocier**.  
  
## Réinitialisation de la disposition des éléments  
 Vous pouvez restaurer les valeurs par défaut de propriétés de disposition spécifiques d'un élément à l'aide des commandes de réinitialisation de la disposition.  À l'aide de ces commandes, vous pouvez réinitialiser la marge, l'alignement, la largeur, la hauteur et la taille d'un élément, individuellement ou collectivement.  
  
#### Pour réinitialiser la disposition des éléments  
  
-   Dans la fenêtre Structure du document ou la planche graphique, cliquez sur l'élément avec le bouton droit, choisissez **Disposition**, **Réinitialiser** *nom\_propriété*, où *nom\_propriété* est la propriété à réinitialiser \(ou choisissez **Disposition**, **Réinitialiser tout** pour réinitialiser toutes les propriétés de disposition de l'élément\).  
  
## Voir aussi  
 [Création d'une interface utilisateur à l'aide du concepteur XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)