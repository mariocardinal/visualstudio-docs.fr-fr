---
title: "Débogage en mode mixte pour Python dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 7/12/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ca86a87-e254-4ab7-b3ba-a0ab99c1da93
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: a185a7888b693d37aa5df8f3a051679d6b7e9ec5
ms.contentlocale: fr-fr
ms.lasthandoff: 07/18/2017

---

# <a name="debugging-python-and-c-together"></a>Débogage conjoint de Python et de C++

La plupart des débogueurs Python standard prend en charge le débogage de code Python uniquement. Toutefois, dans la pratique, Python est utilisé conjointement avec C ou C++ dans les cas qui nécessitent de hautes performances ou la possibilité d’appeler directement les API de plateforme (pour obtenir un exemple, consultez [Création d’une extension C++ pour Python](cpp-and-python.md)). Quand un projet Python est chargé, Visual Studio intègre un débogage en mode mixte simultané de code Python et C/C++ natif, incluant des piles des appels combinées, la possibilité d’effectuer un pas à pas détaillé alternant entre du code Python et natif, des points d’arrêt dans l’un ou l’autre type de code, ainsi que la possibilité de visualiser des représentations Python des objets dans des cadres natifs et vice versa :

![Débogage en mode mixte](media/mixed-mode-debugging.png) 

Pour découvrir une présentation de la génération, du test et du débogage de modules C natifs avec Visual Studio, visionnez la vidéo [Deep Dive: Creating Native Modules](https://youtu.be/D9RlT06a1EI) (Exploration de la création de modules natifs), (youtube.com, 9 mn 9 s).

> [!VIDEO https://www.youtube.com/embed/D9RlT06a1EI]

> [!Note]
> Le débogage en mode mixte n’est pas disponible avec Python Tools pour Visual Studio 1.x.

## <a name="enabling-mixed-mode-debugging"></a>Activation du débogage en mode mixte

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet, sélectionnez **Propriétés**, sélectionnez l’onglet **Débogage**, puis activez l’option **Permettre le débogage du code natif**. Cette option active le mode mixte pour toutes les sessions de débogage.

    ![Activation du débogage du code natif](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]    
    > Quand vous activez le débogage du code natif, la fenêtre de sortie Python peut disparaître immédiatement une fois le programme terminé sans afficher la pause habituelle « Appuyez sur une touche pour continuer... ». Pour forcer une pause, ajoutez l’option `-i` au champ **Exécuter > Arguments de l’interpréteur** sous l’onglet **Déboguer** quand vous activez le débogage du code natif. Avec cet argument, l’interpréteur Python passe en mode interactif à la fin du code, où il attend que vous appuyiez sur Ctrl+Z, Entrée pour quitter.

1. Lorsque vous attachez le débogueur en mode mixte à un processus existant (**Débogage > Attacher au processus...**), sélectionnez le bouton **Sélectionner...** pour ouvrir la boîte de dialogue **Sélectionner le type de code**, activez l’option **Déboguer ces types de codes**, puis sélectionnez à la fois **Natif** et **Python** dans la liste :

    ![Sélection des types de codes Natif et Python](media/mixed-mode-debugging-code-type.png)

    Les paramètres de type de code sont persistants. Par conséquent, si vous souhaitez désactiver le débogage en mode mixte lors de l’attachement à un autre processus par la suite, vous devrez répéter ces étapes et désélectionner le type de code Python.

    Vous pouvez sélectionner d’autres types de codes, en plus ou au lieu du type **Natif**. Par exemple, si une application managée héberge CPython, qui utilise lui-même des modules d’extension natifs, et que vous souhaitez les déboguer tous les trois, vous pouvez sélectionner les types **Python**, **Natif** et Managé** afin de bénéficier d’une expérience de débogage unifiée incluant des piles des appels combinées et l’exécution d’un débogage pas à pas portant sur les trois runtimes simultanément.

1. Quand vous démarrez un débogage en mode mixte pour la première fois, une boîte de dialogue **Symboles Python obligatoires** peut s’afficher. Pour plus d’informations, consultez [Symboles de débogage en mode mixte](debugging-symbols-for-mixed-mode.md). Vous ne devez installer les symboles qu’une seule fois pour un environnement Python donné. Notez que, si vous installez la prise en charge de Python par le biais du programme d’installation de Visual Studio 2017, les symboles sont automatiquement inclus.

1. Vous voudrez peut-être aussi disposer du code source Python proprement dit. Vous pouvez obtenir le code source Python standard à l’adresse [https://www.python.org/downloads/source/](https://www.python.org/downloads/source/). Téléchargez l’archive appropriée à votre version et extrayez-la dans un dossier. Faites ensuite pointer Visual Studio vers des fichiers spécifiques dans ce dossier quand il vous le demande.

> [!Note]
> Le débogage en mode mixte tel qu’il est décrit ici est uniquement activé quand un projet Python est chargé dans Visual Studio. Ce projet détermine le mode de débogage de Visual Studio, lequel active l’option de débogage en mode mixte. Si, toutefois, un projet C++ est chargé (ce qui se produit en cas d’[incorporation de Python dans une autre application, comme décrit sur python.org](https://docs.python.org/3/extending/embedding.html)), Visual Studio utilise le débogueur C++ natif qui ne prend pas en charge le débogage en mode mixte.
>
> Dans ce cas, démarrez le projet C++ sans débogage (**Déboguer > Démarrer sans débogage** ou Ctrl+F5), puis utilisez **Déboguer > Attacher au processus**. Dans la boîte de dialogue qui s’affiche, sélectionnez le processus approprié, puis utilisez le bouton **Sélectionner** pour ouvrir la boîte de dialogue **Sélectionner le type de code**. Dans celle-ci, sélectionnez Python (comme indiqué ci-dessous). Sélectionnez **OK** pour fermer cette boîte de dialogue, puis sélectionnez **Attacher** pour démarrer le débogueur. Notez que vous devrez peut-être introduire une pause ou un délai approprié dans l’application C++ pour que celle-ci n’appelle pas le code Python à déboguer avant l’attachement du débogueur.
>
> ![Sélection de Python comme type de débogage au moment de l’attachement d’un débogueur](media/mixed-mode-debugging-attach-type.png)

## <a name="mixed-mode-specific-features"></a>Fonctionnalités spécifiques du mode mixte

- [Pile des appels combinée](#combined-call-stack)
- [Pas à pas détaillé alternant entre code Python et natif](#stepping-between-python-and-native-code)
- [Vue des valeurs PyObject dans le code natif](#pyobject-values-view-in-native-code)
- [Vue des valeurs natives dans le code Python](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>Pile des appels combinée

La fenêtre Pile des appels affiche des frames de pile natifs et Python entrelacés, en insérant des transitions entre les deux :

![Pile des appels combinée](media/mixed-mode-debugging-call-stack.png)

> [!Note]
> Si l’option **Outils > Options > Débogage > Général > Activer Uniquement mon code** est définie, les transitions apparaissent sous la forme « [Code externe] », sans spécifier la direction de la transition.

Un double-clic sur un frame d’appel quelconque active ce dernier et ouvre le code source approprié, si cela est possible. Si le code source n’est pas disponible, le frame est quand même activé et les variables locales peuvent être inspectées.

### <a name="stepping-between-python-and-native-code"></a>Pas à pas détaillé alternant entre code Python et natif

Lorsque vous utilisez les commandes Pas à pas détaillé (F11) ou Pas à pas sortant (Maj+F11), le débogueur en mode mixte gère correctement l’alternance entre ces types de codes. Par exemple, lorsque Python appelle une méthode d’un type implémenté en C, le pas à pas détaillé sur un appel de cette méthode s’arrête au début de la fonction native implémentant la méthode. De même, lorsqu’un code natif appelle une fonction API Python, un code Python est appelé. Par exemple, l’exécution d’un pas à pas détaillé dans `PyObject_CallObject` sur une valeur de fonction initialement définie dans Python s’arrête au début de la fonction Python. L’exécution d’un pas à pas détaillé alternant entre un code Python et natif est également prise en charge pour les fonctions natives appelées à partir de Python par le biais de [ctypes](http://docs.python.org/3/library/ctypes.html).

### <a name="pyobject-values-view-in-native-code"></a>Vue des valeurs PyObject dans le code natif

Lorsqu’un frame natif (C ou C++) est actif, ses variables locales s’affichent dans la fenêtre Variables locales du débogueur. Dans les modules d’extension Python natifs, de nombreuses variables sont de type `PyObject` (qui est un typedef de `_object`), ou de quelques autres types Python fondamentaux (consultez la liste ci-dessous). Dans le cadre du débogage en mode mixte, ces valeurs présentent un nœud enfant supplémentaire intitulé « Python view » (Vue Python). Quand ce nœud est développé, il affiche la représentation Python de la variable, telle qu’elle apparaîtrait si une variable locale référençant le même objet était présente dans un frame Python. Les enfants de ce nœud sont modifiables.

![Vue Python](media/mixed-mode-debugging-python-view.png)

Pour désactiver cette fonctionnalité, cliquez avec le bouton droit sur un emplacement quelconque de la fenêtre Variables locales, puis désélectionnez l’option de menu **Python > Show Python View Nodes (Afficher les nœuds de vue Python)** :

![Activation de la vue Python](media/mixed-mode-debugging-enable-python-view.png)

Types C affichant les nœuds « [Python View] » (Vue Python) (si cette option est activée) :

- `PyObject `
- `PyVarObject`
- `PyTypeObject`
- `PyByteArrayObject`
- `PyBytesObject`
- `PyTupleObject`
- `PyListObject`
- `PyDictObject`
- `PySetObject`
- `PyIntObject`
- `PyLongObject`
- `PyFloatObject`
- `PyStringObject`
- `PyUnicodeObject`

« [Python View] » (Vue Python) n’apparaît pas automatiquement pour les types que vous créez vous-même. Quand vous créez des extensions pour Python 3.x, ceci n’est généralement pas un problème, car tout objet comporte au final un champ `ob_base` de l’un des types ci-dessus, ce qui entraîne l’apparition des nœuds « [Vue Python] ». 

Toutefois, pour Python 2.x, chaque type d’objet déclare généralement son en-tête sous la forme d’une collection de champs inline, et il n’existe aucune association entre les types créés personnalisés et `PyObject` au niveau du système de type en code C/C++. Pour activer les nœuds « [Vue Python] » pour de tels types personnalisés, modifiez le fichier `PythonDkm.natvis` dans le [répertoire d’installation de Python Tools](installation.md#install-locations), et ajoutez un autre élément dans le code XML pour votre struct C ou classe C++.

Une autre option (mieux adaptée) consiste à suivre la spécification [PEP 3123](http://www.python.org/dev/peps/pep-3123/) et à utiliser un champ `PyObject ob_base;` explicite plutôt que `PyObject_HEAD`, bien que cette opération ne soit pas toujours possible pour des raisons de compatibilité descendante.


### <a name="native-values-view-in-python-code"></a>Vue des valeurs natives dans le code Python

Comme dans la section précédente, vous pouvez activer un nœud « [C++ View] » (Vue C++) pour les valeurs natives dans la fenêtre Variables locales lorsqu’un frame Python est actif. Cette fonctionnalité est désactivée par défaut. Si vous souhaitez l’activer, cliquez avec le bouton droit dans la fenêtre Variables locales, puis sélectionnez l’option **Python > Show C++ View Nodes (Afficher les nœuds de vue C++)**.

![Activation de la vue C++](media/mixed-mode-debugging-enable-cpp-view.png)

Le nœud « [Vue C++] » fournit une représentation de la structure C/C++ sous-jacente d’une valeur, telle qu’elle apparaîtrait dans un frame natif. Par exemple, il affiche une instance de `_longobject` (dont `PyLongObject` est un typedef) pour un entier long Python, et il essaie de déduire les types des classes natives que vous avez vous-même créées. Les enfants de ce nœud sont modifiables.

![Vue C++](media/mixed-mode-debugging-cpp-view.png)

Si un champ enfant d’un objet est du type `PyObject` ou de l’un des autres types pris en charge, il comporte un nœud de représentation « [Vue Python] » (si ces représentations sont activées), ce qui offre la possibilité de parcourir les graphiques d’objet quand les liens ne sont pas directement exposés à Python.

Contrairement aux nœuds « [Python View] » (Vue Python), qui utilisent les métadonnées d’objet Python pour déterminer le type de l’objet, il n’existe aucun mécanisme suffisamment fiable pour « [C++ View] » (Vue C++). En règle générale, pour une valeur Python donnée (autrement dit, une référence `PyObject`) il est impossible de déterminer avec certitude la structure C/C++ sous-jacente. Le débogueur en mode mixte tente de déduire ce type en examinant les différents champs du type de l’objet (comme l’élément `PyTypeObject` référencé par son champ `ob_type`) qui comportent des types de pointeur fonction. Si l’un de ces pointeurs fonction référence une fonction qui peut être résolue, et que cette fonction comporte un paramètre `self` avec un type plus spécifique que `PyObject*`, ce type est considéré comme le type de stockage. Par exemple, si l’élément `ob_type->tp_init` d’un objet donné pointe vers la fonction suivante :

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

le débogueur peut correctement en déduire que le type C de l’objet est `FobObject`. S’il ne parvient pas à déterminer un type plus précis en fonction de `tp_init`, il passe aux autres champs. S’il lui est impossible de déduire le type d’après l’ensemble de ces champs, le nœud « [C++ View] » (Vue C++) présente l’objet sous la forme d’une instance `PyObject`.

Pour obtenir systématiquement une représentation utile pour les types créés personnalisés, il est préférable d’inscrire au moins une fonction spéciale lors de l’inscription du type et d’utiliser un paramètre `self` fortement typé. La plupart des types répondent automatiquement à cette exigence ; dans le cas contraire, `tp_init` constitue généralement l’entrée la plus simple à utiliser dans ce but. Une implémentation factice de `tp_init` pour un type servant uniquement à permettre la déduction du type de débogueur peut simplement renvoyer immédiatement la valeur zéro, comme dans l’exemple de code ci-dessus.

## <a name="differences-from-standard-python-debugging"></a>Différences par rapport au débogage Python standard

Le débogueur en mode mixte se différencie du [débogueur Python standard](debugging.md) par le fait qu’il offre certaines fonctionnalités supplémentaires, tout en étant dépourvu de certaines capacités associées à Python :

- Fonctionnalités non prises en charge : points d’arrêt conditionnels, fenêtre de débogage interactive et débogage à distance multiplateforme.
- Fenêtre Exécution : disponible mais avec un sous-ensemble de fonctionnalités restreint, incluant notamment toutes les limitations répertoriées dans cette section.
- Versions Python prises en charge : CPython 2.7, 3.3 et versions ultérieures uniquement.
- Visual Studio Shell : lorsque vous utilisez Python avec Visual Studio Shell (par exemple, si vous l’avez installé à l’aide du programme d’installation intégré), Visual Studio n’est pas en mesure d’ouvrir les projets C++, et l’expérience de modification des fichiers C++ se limite à celle d’un éditeur de texte de base. Toutefois, le débogage C/C++ et le débogage en mode mixte sont entièrement pris en charge dans Shell avec le code source, l’exécution d’un pas à pas détaillé dans le code natif et l’évaluation des expressions C++ dans les fenêtres de débogage.
- Visualisation et développement d’objets : lorsque vous visualisez des objets Python dans les fenêtres d’outil de débogage Variables locales et Espion, le débogueur en mode mixte présente uniquement la structure des objets. Il n’évalue pas automatiquement les propriétés et n’affiche pas les attributs calculés. Dans le cas des collections, il présente uniquement les éléments pour les types de collections intégrés (`tuple`, `list`, `dict`, `set`). Les types de collections personnalisés ne sont pas visualisés sous forme de collections, sauf s’ils sont hérités d’un type de collection intégré.
- Évaluation des expressions : voir ci-dessous.

### <a name="expression-evaluation"></a>Évaluation des expressions

Le débogueur Python standard autorise l’évaluation des expressions Python arbitraires dans les fenêtres Espion et Exécution lorsque le processus débogué est suspendu au niveau d’un emplacement quelconque dans le code, à condition qu’il ne soit pas bloqué dans une opération d’E/S ou dans un autre appel système similaire. Dans le cadre du débogage en mode mixte, les expressions arbitraires ne peuvent être évaluées qu’en cas d’arrêt dans le code Python, après un point d’arrêt ou lors d’un pas à pas détaillé dans le code. Les expressions ne peuvent être évaluées que sur le thread sur lequel le point d’arrêt ou l’opération pas à pas se sont produits.

Lors d’un arrêt dans le code natif, ou dans le code Python lorsque les conditions ci-dessus ne s’appliquent pas (par exemple, après une opération de pas à pas sortant, ou sur un autre thread), l’évaluation des expressions se limite à accéder aux variables locales et globales dans la portée du frame actuellement sélectionné, à accéder aux champs de ces variables et à indexer les types de collections intégrés avec des littéraux. Par exemple, l’expression ci-après peut être évaluée dans n’importe quel contexte (à condition que tous les identificateurs référencent des variables existantes et des champs des types appropriés) :

```python
foo.bar[0].baz['key']
```

Le débogueur en mode mixte résout également de telles expressions d’une autre manière. Toutes les opérations d’accès aux membres recherchent uniquement les champs qui font directement partie intégrante de l’objet (tels qu’une entrée dans ses éléments `__dict__` ou `__slots__`, ou un champ d’un struct natif exposé à Python par le biais de `tp_members`), et ignorent tout élément `__getattr__`, `__getattribute__` ou toute logique de descripteur. De même, toutes les opérations d’indexation ignorent `__getitem__` et accèdent directement aux structures de données internes des collections.

Par souci de cohérence, ce schéma de résolution de noms est utilisé pour toutes les expressions qui correspondent aux contraintes relatives à l’évaluation des expressions limitée, que les expressions arbitraires soient ou non autorisées au niveau du point d’arrêt actuel. Pour imposer la sémantique Python appropriée lorsqu’un évaluateur complet est disponible, indiquez l’expression entre parenthèses :

```python
(foo.bar[0].baz['key'])
```
