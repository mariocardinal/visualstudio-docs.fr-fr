---
title: Typedefs de Visual C++ dans le Concepteur de classes | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
caps.latest.revision: 12
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: efaec77b5d3a2fb52859ff08fe31aa6f35e4263b
ms.lasthandoff: 02/22/2017

---
# <a name="visual-c-typedefs-in-class-designer"></a>Typedefs de Visual C++ dans le Concepteur de classes
Les instructions typedef créent une ou plusieurs couches d’indirection entre un nom et son type sous-jacent. Le Concepteur de classes prend en charge les types typedef C++ qui sont déclarés avec le mot clé `typedef`, par exemple :  
  
```  
typedef class coord  
{  
   void P(x,y);  
   unsigned x;  
   unsigned y;  
} COORD;  
```  
  
 Vous pouvez ensuite utiliser ce type pour déclarer une instance :  
  
 `COORD OriginPoint;`  
  
 Bien que vous puissiez déclarer un typedef sans nom, le Concepteur de classes n’utilisera pas le nom de la balise que vous spécifiez ; il utilisera le nom généré par l’affichage de classes. Par exemple, la déclaration suivante est valide, mais elle apparaît dans l’affichage de classes et le Concepteur de classes en tant qu’objet nommé **__unnamed** :  
  
```  
typedef class coord  
{  
   void P(x,y);  
   unsigned x;  
   unsigned y;  
};  
```  
  
 Pour plus d’informations sur l’utilisation du type `typedef`, consultez [(NOTINBUILD)typedef, spécificateur](http://msdn.microsoft.com/en-us/cc96cf26-ba93-4179-951e-695d1f5fdcf1).  
  
 Une forme typedef C++ a la forme du type spécifié dans le typedef. Par exemple, si la source déclare `typedef class`, la forme a des angles arrondis et l’étiquette **Class**. Pour `typedef struct`, la forme a des angles carrés et l’étiquette **Struct**.  
  
 Les classes et les structures peuvent avoir des typedefs imbriqués déclarés à l’intérieur. Ainsi, les formes de classe et de structure peuvent afficher des déclarations typedef imbriquées comme formes imbriquées.  
  
 Les formes typedef prennent en charge les commandes **Afficher en tant qu’association** et **Afficher en tant qu’association de collection** dans le menu contextuel.  
  
 Voici quelques exemples de types typedef pris en charge par le Concepteur de classes :  
  
 `typedef type name`  
  
 *nom* : *type*  
  
 typedef  
  
 Dessine une ligne d’association établissant une connexion au type *nom*, si possible.  
  
 `typedef void (*func)(int)`  
  
 `func: void (*)(int)`  
  
 typedef  
  
 Typedef pour les pointeurs de fonction. Aucune ligne d’association n’est dessinée.  
  
 Le Concepteur de classes n’affiche pas de typedef si son type source est un pointeur de fonction.  
  
```  
typedef int MyInt;  
class A {  
   MyInt I;  
};  
```  
  
 `MyInt: int`  
  
 typedef  
  
 `A`  
  
 Class  
  
 Dessine une ligne d’association qui pointe de la forme du type source vers la forme du type cible.  
  
 `Class B {};`  
  
 `typedef B MyB;`  
  
 `B`  
  
 Class  
  
 `MyB : B`  
  
 typedef  
  
 Un clic droit sur une forme typedef et un clic sur **Afficher en tant qu’association** affiche le typedef ou la classe et une ligne **Alias** reliant les deux formes (semblable à une ligne d’association).  
  
 `typedef B MyB;`  
  
 `typedef MyB A;`  
  
 `MyBar : Bar`  
  
 typedef  
  
 Identique à ce qui précède.  
  
```  
Class B {};  
typedef B MyB;  
  
class A {  
   MyB B;  
};  
```  
  
 `B`  
  
 Class  
  
 `MyB : B`  
  
 typedef  
  
 `A`  
  
 Class  
  
 `MyB` est une forme typedef imbriquée.  
  
 `#include <vector>`  
  
 `...`  
  
 `using namespace std;`  
  
 `...`  
  
 `typedef vector<int> MyIntVect;`  
  
 `vector<T>`Class  
  
 `MyIntVect : vector<int>`  
  
 typedef  
  
 `class B {};`  
  
 `typedef B MyB;`  
  
 `class A : MyB {};`  
  
 `MyB : B`  
  
 typedef  
  
 -> B  
  
 `B`  
  
 `A`  
  
 Class  
  
 -> MyB  
  
 Le Concepteur de classes ne prend pas en charge l’affichage de ce type de relation à l’aide d’une commande de menu contextuel.  
  
 `#include <vector>`  
  
 `Typedef MyIntVect std::vector<int>;`  
  
 `Class MyVect : MyIntVect {};`  
  
 `std::vector<T>`  
  
 Class  
  
 `MyIntVect : std::vector<int>`  
  
 typedef  
  
 `MyVect`  
  
 Class  
  
 -> MyIntVect  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du code Visual C++ (Concepteur de classes)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [(NOTINBUILD)typedef, spécificateur](http://msdn.microsoft.com/en-us/cc96cf26-ba93-4179-951e-695d1f5fdcf1)
