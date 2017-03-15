---
title: "Concepts de base du d&#233;bogage&#160;: fen&#234;tre Registres | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Registres (fenêtre), à propos de la fenêtre Registres"
  - "débogage (Visual Studio), fenêtre Registres"
ms.assetid: ab354047-053e-4f94-8ac1-26e761442b6f
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Concepts de base du d&#233;bogage&#160;: fen&#234;tre Registres
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La fenêtre **Registres** n'est disponible que si le débogage au niveau de l'adresse est activé dans la boîte de dialogue **Options**, nœud **Débogage**.  
  
 Les registres sont des emplacements particuliers dans un processeur \(UC\) qui sont utilisés pour stocker de petits fragments de données sur lesquels le processeur travaille activement.  La compilation ou l'interprétation du code source génère des instructions qui déplacent des données de la mémoire vers des registres et vice versa, en fonction des besoins.  L'accès aux données stockées dans les registres est très rapide comparé à l'accès aux données stockées en mémoire. De ce fait, le code autorisant le processeur à stocker des données dans un Registre et à y accéder à maintes reprises tend à s'exécuter plus rapidement que le code exigeant que le processeur charge et décharge constamment les registres.  Pour que le compilateur puisse plus facilement conserver des données dans des registres et réaliser d'autres optimisations, vous devez éviter d'utiliser des variables globales et utiliser autant que possible des variables locales.  Le code écrit de cette manière est réputé avoir une bonne localité de référence.  Dans certains langages, tels que C\/C\+\+, le programmeur peut déclarer une variable de Registre qui demande au compilateur de faire de son mieux pour essayer de toujours conserver la variable dans un Registre.  Pour plus d'informations, consultez [Register, mot clé](http://msdn.microsoft.com/fr-fr/5b66905a-2f7f-4918-bb55-5e66d4bc50f9).  
  
 Les registres peuvent être divisés en deux types : les registres génériques et les registres spéciaux.  Les registres à caractère général contiennent des données relatives à des opérations générales telles que l'ajout de deux nombres ou la référence d'un élément dans un tableau.  Les registres spéciaux ont des buts spécifiques et une signification particulière.  Le Registre de pointeur de pile en est un bon exemple ; il est utilisé par le processeur pour conserver une trace de la pile des appels du programme.  En tant que programmeur, vous ne manipulerez probablement pas directement le pointeur de pile.  Il est néanmoins essentiel au bon fonctionnement de votre programme, car en son absence, le processeur ne sait pas où revenir à l'issue d'un appel de fonction.  
  
 La plupart des registres à caractère général contiennent uniquement un élément de données.  Par exemple, un entier seul, un nombre à virgule flottante ou un élément d'un tableau.  Certains processeurs plus récents proposent des registres de plus grande taille, appelés des registres vectoriels, qui peuvent contenir un petit tableau de données.  Du fait de leurs nombreuses données, les registres vectoriels permettent d'effectuer rapidement les opérations impliquant des tableaux.  Ces registres ont dans un premier temps été utilisés sur les superordinateurs très performants et coûteux, mais commencent à apparaître sur les microprocesseurs où ils s'avèrent tout particulièrement utiles dans les opérations complexes sur les graphiques.  
  
 Un processeur contient généralement deux jeux de registres à caractère général, un qui est optimisé pour les opérations en virgule flottante et un second pour les opérations sur les entiers.  Logiquement, ils sont appelés Registre à virgule flottante et Registre entier.  
  
 Le code managé est compilé pendant l'exécution en code natif, qui accède aux registres physiques du microprocesseur.  La fenêtre **Registres** affiche ces registres physiques pour le common language runtime ou le code natif.  La fenêtre **Registres** n'affiche pas d'informations de registre pour le script ou l'application SQL, parce que le script et SQL sont des langages qui ne prennent pas en charge le concept de registres.  
  
 Pour plus d'informations sur l'affichage de la fenêtre **Registres**, consultez [Utilisation de la fenêtre Registres](../debugger/how-to-use-the-registers-window.md).  
  
 Dans la fenêtre **Registres**, vous pouvez consulter des entrées telles que cet exemple :  
  
```  
EAX = 003110D8  
```  
  
 Le symbole à gauche du signe \= est le nom de registre, EAX, dans ce cas.  Le nombre à droite du signe \= représente le contenu du Registre.  
  
 La fenêtre **Registres** vous permet de faire plus que simplement afficher le contenu d'un registre.  Lorsque vous êtes en mode arrêt dans du code natif, vous pouvez cliquer sur le contenu d'un Registre et modifier la valeur.  Cette opération ne doit pas être réalisée à l'aveuglette.  Sauf si vous comprenez le Registre que vous êtes en train de modifier et les données qu'il contient, la modification inconsidérée peut provoquer un incident du programme ou avoir d'autres conséquences non désirées.  Malheureusement, l'explication détaillée des jeux de registres des différents processeurs Intel et compatibles va bien au\-delà de l'objet de cette brève introduction.  
  
## Groupes de registres  
 Pour des raisons de clarté, la fenêtre **Registres** classe les registres en groupes.  Si vous cliquez avec le bouton droit sur la fenêtre **Registres**, un menu contextuel contenant une liste des groupes s'affiche. Vous pouvez afficher ou masquer des groupes selon vos besoins.  
  
## Voir aussi  
 [Comment : utiliser la fenêtre Registres](../debugger/how-to-use-the-registers-window.md)   
 [Principes de base du débogueur](../debugger/debugger-basics.md)