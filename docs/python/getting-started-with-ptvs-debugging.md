---
title: "Prise en main des outils Python pour Visual Studio&#160;: d&#233;bogage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-python"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82803559-1d60-4c57-98fb-2dc1e0182b42
caps.latest.revision: 4
author: "kraigb"
ms.author: "kraigb"
manager: "ghogen"
caps.handback.revision: 4
---
# Prise en main des outils Python pour Visual Studio&#160;: d&#233;bogage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le débogueur interactif de Visual Studio facilite le diagnostic et la résolution des problèmes dans votre code Python.  
  
 Vous pouvez voir ces instructions dans une très courte [vidéo youtube](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4).  
  
 Dans la rubrique précédente de prise en main, vous avez créé un projet d'application Python vide et vous avez entré le code suivant dans PythonApplication1.py :  
  
```python  
from math import sin, cos, radians  
import sys  
  
def make_dot_string(x):  
    return ' ' * int(10 * cos(radians(x)) + 10) + 'o'  
  
assert make_dot_string(90) == "          o"  
assert make_dot_string(180) == "o"  
  
def main():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
  
if __name__ == "__main__":  
    sys.exit(int(main() or 0))  
```  
  
 Normalement, quand vous travaillez sur le code dans Visual Studio, vous lancez l'exécution de votre code en appuyant sur F5.  Cette commande génère tous les composants de votre projet qui doivent l'être et démarre l'exécution du code sous le débogueur.  Vous pouvez appuyer sur Ctrl\+F5 pour générer et lancer votre code sans le débogueur.  Avec le débogueur, votre code s'exécute un peu plus lentement, mais vous bénéficiez en échange d'excellentes fonctionnalités de débogage.  
  
 Une autre façon de lancer votre code est d'utiliser la commande Pas à pas détaillé \(normalement associée à F11\).  Elle est similaire à F5, mais elle suspend l'exécution à chaque instruction.  Si vous voulez interrompre le programme à un certain point, vous pouvez appuyer sur le bouton du pointeur de gauche dans la marge gauche de l'éditeur de code pour définir un point d'arrêt.  Quand vous appuyez sur F5, l'exécution du programme s'interrompt ou s'arrête à la ligne avec le point d'arrêt.  Le menu Débogage a davantage d'options pour l'exécution pas à pas ; par exemple, passer les appels de fonction \(F10\), exécuter pas à pas les appels de fonction \(F11\) ou passer directement à la fin d'une fonction \(Maj\+F11\).  
  
 Vous pouvez faire d'autres choses lors d'un arrêt de l'exécution du code dans le débogueur.  La fenêtre Variables locales montre les valeurs actuelles des variables locales.  Au fil de votre progression pas à pas dans le code, l'affichage des variables locales se met automatiquement à jour.  La fenêtre Automatique montre les variables près de la ligne actuelle où l'exécution s'est arrêtée.  Dans la fenêtre Espion, vous pouvez taper n'importe quelle expression Python : le débogueur la met alors automatiquement à jour chaque fois que l'exécution s'arrête.  Vous pouvez également placer le pointeur sur des variables dans les fenêtres de l'éditeur pour afficher les valeurs de la variable dans une fenêtre contextuelle. Cet affichage sous forme de bulle d'informations vous permet d'examiner des objets.  Certains types de données ont des visualiseurs spéciaux qui sont accessibles à partir des bulles d'informations \(par exemple des chaînes avec une mise en forme spéciale, comme HTML, XML ou JSON\).  
  
 La fenêtre Pile des appels montre les appels de fonction en attente qui ont conduit à l'instruction actuelle où le débogueur est arrêté.  Vous pouvez choisir différentes frames de pile \(les lignes dans la pile des appels\) pour accéder à l'endroit où le code continuera de s'exécuter dans chaque fonction, examiner la valeur des variables, etc.  
  
 Vous pouvez voir ces instructions dans une très courte [vidéo youtube](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4).  
  
## Voir aussi  
 [Documentation Wiki](https://github.com/Microsoft/PTVS/wiki/Debugging)   
 [Vidéos de prise en main et de présentation approfondie de PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)