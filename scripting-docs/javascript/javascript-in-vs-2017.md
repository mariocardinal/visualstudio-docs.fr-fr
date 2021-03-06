---
title: JavaScript dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 04/10/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 74dca14c-5071-416f-a92b-d09f95e3dfb8
caps.latest.revision: "1"
author: bowdenk7
ms.author: wilkelly
manager: ghogen
ms.openlocfilehash: d217443ed0231d71f861ed54b27f3f8d1e8d49ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="javascript-in-includevsdev15docsmiscincludesvsdev15mdmd"></a>JavaScript dans [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)]

JavaScript est un langage de premier ordre dans Visual Studio. Vous pouvez utiliser la plupart ou toutes les aides standard de modification (extraits de code, IntelliSense, etc.) lorsque vous écrivez du code JavaScript dans l'IDE de Visual Studio. Vous pouvez écrire du code JavaScript pour de nombreux types d'applications et services.

## <a name="ES6"></a> Prise en charge d’ECMAScript 2015 (ES6) et ultérieur
Visual Studio prend désormais en charge la syntaxe des mises à jour de langage ECMAScript, par exemple ECMAScript 2015/2016.

### <a name="what-is-ecmascript-2015"></a>En quoi consiste ECMAScript 2015 ?

JavaScript est un langage de programmation en constante évolution, et [TC39](http://www.ecma-international.org/memento/TC39.htm) est le comité en charge des mises à jour.  
ECMAScript 2015 est une mise à jour du langage JavaScript qui introduit un grand nombre de fonctionnalités et d’éléments de syntaxe utiles.
Pour une présentation approfondie des fonctionnalités d’ES6, consultez [ce site de référence](http://es6-features.org).

Outre ECMAScript 2015, Visual Studio prend en charge ECMAScript 2016 et toutes les nouvelles versions d’ECMAScript dès leur publication. Pour vous tenir informé des derniers changements dans ECMAScript, suivez les travaux de TC39 sur [github](https://github.com/tc39).

### <a name="transpiling-javascript"></a>Transpilation de JavaScript

Le problème qui revient souvent avec JavaScript, c’est que les dernières fonctionnalités du langage ES6+ qui vous aident à être plus productif ne sont pas prises en charge par vos environnements d’exécution (souvent des navigateurs).
Vous devez donc soit déterminer les fonctionnalités prises en charge par les navigateurs (ce qui peut être fastidieux), soit trouver un moyen de convertir votre code ES6+ en une version comprise par vos runtimes cibles (en général ES5).
C’est ce qu’on appelle communément la « transpilation ».

L’une des fonctionnalités clés de TypeScript est la possibilité de transpiler du code ES6+ vers ES5 ou ES3. Vous pouvez ainsi écrire du code qui optimise votre productivité et l’exécuter sur n’importe quelle plateforme.  
Étant donné que JavaScript dans [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] utilise le même service de langage que TypeScript, il peut également tirer parti de la transpilation d’ES6+ vers ES5.

Avant de mettre en place ce paramétrage, vous devez comprendre les options de configuration. TypeScript est configuré par le biais d’un fichier `tsconfig.json`. En l’absence de ce fichier, certaines valeurs par défaut sont utilisées. Pour des raisons de compatibilité, ces valeurs sont différentes si seuls sont présents des fichiers JavaScript (et, éventuellement, des fichiers `.d.ts`). Pour compiler des fichiers JavaScript, vous devez ajouter un fichier `tsconfig.json` et définir explicitement certaines de ces options.

Les paramètres requis pour le fichier tsconfig sont décrits ci-dessous :

 - `allowJs` : cette valeur doit être définie sur `true` pour les fichiers JavaScript à reconnaître.
TypeScript étant compilé en JavaScript, la valeur par défaut est `false`, afin que le compilateur n’inclue pas les fichiers qu’il vient de compiler.
 - `outDir` : vous devez définir ce paramètre sur un emplacement non inclus dans le projet, afin que les fichiers JavaScript émis ne soient pas détectés, puis inclus dans le projet (voir `exclude` ci-après).
 - `module` : si vous utilisez des modules, ce paramètre indique au compilateur le format de module que le code émis doit utiliser (par exemple, `commonjs` pour Node ou des outils de regroupement tels que Browserify).
 - `exclude` : ce paramètre indique les dossiers à ne pas inclure dans le projet. 
 L’emplacement de sortie, ainsi que les dossiers autres que les dossiers de projet tels que `node_modules` ou `temp`, doivent être ajoutés à ce paramètre.
 - `enableAutoDiscovery` : ce paramètre permet de détecter et télécharger automatiquement les fichiers de définition comme indiqué plus haut.
 - `compileOnSave` : ce paramètre indique au compilateur s’il doit réexécuter la compilation chaque fois qu’un fichier source est enregistré dans Visual Studio.
 - `typeAcquisition` : cet ensemble de paramètres contrôle le comportement de l’acquisition de type automatique (pour plus de détails, consultez [cette section](https://docs.microsoft.com/en-us/visualstudio/ide/javascript-intellisense#Auto)).

Pour convertir des fichiers JavaScript en modules CommonJS et les placer dans un dossier `./out`, vous pouvez utiliser le fichier `tsconfig.json` suivant.

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "allowJs": true,
    "outDir": "out"
  },
  "exclude": [
    "node_modules",
    "wwwroot",
    "out"
  ],
  "compileOnSave": true,
  "typeAcquisition": {
    "enable": true
  }
}
```

Une fois les paramètres ci-dessus en place, s’il existe un fichier source (`./app.js`) qui contient plusieurs fonctionnalités de langage ECMAScript 2015 comme indiqué ci-dessous :

```js
import {Subscription} from 'rxjs/Subscription';  // ES6 import

class Foo {  // ES6 Class
    sayHi(name) {
        return `Hi ${name}, welcome to Salsa!`;  // ES6 template string
    }
}

export let sqr = x => x * x;  //ES6 export, let, and arrow function
export default Subscription;  //ES6 default export
```

Un fichier tel que celui ci-après ciblant ECMAScript 5 (paramétrage par défaut) est émis vers `./out/app.js` :

```js
"use strict";
var Subscription_1 = require('rxjs/Subscription');
var Foo = (function () {
    function Foo() {
    }
    Foo.prototype.sayHi = function (name) {
        return "Hi " + name + ", welcome to Salsa!";
    };
    return Foo;
}());
exports.sqr = function (x) { return x * x; };
Object.defineProperty(exports, "__esModule", { value: true });
exports.default = Subscription_1.Subscription;
```

## <a name="better-intellisense"></a>Fonctionnalités IntelliSense améliorées

JavaScript IntelliSense dans [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] affiche désormais beaucoup plus d’informations sur les listes de paramètres et de membres. Ces nouvelles informations sont fournies par le service de langage TypeScript, qui utilise l’analyse statique en arrière-plan pour mieux comprendre votre code. Vous trouverez plus d’informations sur la nouvelle expérience IntelliSense et son fonctionnement [ici](/visualstudio/ide/javascript-intellisense/).

## <a name="JSX"></a> Prise en charge de la syntaxe JSX

JavaScript dans [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] offre une prise en charge étendue de la syntaxe JSX. JSX est un ensemble de syntaxes qui autorise les balises HTML dans les fichiers JavaScript. 

L’illustration suivante montre un composant React défini dans le fichier TypeScript `comps.tsx`, puis utilisé à partir du fichier `app.jsx`, où il est possible de recourir à IntelliSense pour les saisies semi-automatiques et la documentation dans les expressions JSX.
Vous n’avez pas besoin de TypeScript ici ; il se trouve simplement que cet exemple contient également du code TypeScript.

<img src="./media/react.png" height="500" width="640"/>

> [!NOTE]
> Pour convertir la syntaxe JSX en appels React, vous devez ajouter le paramètre `"jsx": "react"` à `compilerOptions` dans le fichier `tsconfig.json` décrit ci-dessus.

Le fichier JavaScript créé à l’emplacement « ./out/app.js » au moment de la génération doit contenir le code :

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

# <a name="configuring-your-javascript-project"></a>Configuration de votre projet JavaScript
Le service de langage, qui repose sur l’analyse statique, analyse votre code source sans réellement l’exécuter pour retourner les résultats d’IntelliSense et proposer d’autres fonctionnalités d’édition.
Par conséquent, plus la quantité et la taille des fichiers inclus dans votre contexte de projet sont importantes, plus la mémoire et le processeur sont mis à contribution durant l’analyse.
Pour cette raison, quelques hypothèses par défaut sont émises sur la forme de votre projet :

- Les listes `package.json` et `bower.json` répertorient les dépendances utilisées par votre projet et sont incluses par défaut dans l’acquisition de type automatique (ATA) <TODO - add link>
- Un dossier `node_modules` de premier niveau contient le code source de la bibliothèque, et son contenu est exclu du contexte du projet par défaut
- Tout autre fichier `.js`, `.jsx`, `.ts` et `.tsx` peut être l’un de *vos propres* fichiers sources et doit être inclus dans le contexte du projet

Dans la plupart des cas, vous pouvez simplement ouvrir votre projet et obtenir de bons résultats avec la configuration de projet par défaut ci-dessus.
Toutefois, dans les projets particulièrement volumineux ou avec des structures de dossier différentes, il peut être souhaitable d’affiner la configuration du service de langage pour mieux cibler vos propres fichiers sources.

## <a name="overriding-defaults"></a>Substitution des valeurs par défaut
Vous pouvez substituer la configuration par défaut ci-dessus en ajoutant un fichier `tsconfig.json` à la racine de votre projet.
Un fichier `tsconfig.json` comprend plusieurs options vous permettant de manipuler le contexte de votre projet.
Certaines d’entre elles sont répertoriées ci-dessous. Pour obtenir le jeu complet de toutes les options disponibles, [consultez le magasin de schémas](http://json.schemastore.org/tsconfig). 

## <a name="important-tsconfigjson-options"></a>Options importantes de `tsconfig.json`

```json
{
  "compilerOptions": {
    "allowJs": true,          // include .js and .jsx in project context (defaults to only .ts and .tsx)
    "noEmit": true            // turns off downlevel compiler
  },
  "files": [],                // list of explicit files to include in the project context. Highest priority.
  "include": [],              // list of folders or glob patterns to include in the project context.
  "exclude": [],              // list of folders or glob patterns to exclude. Overridden by files array.
  "typeAcquisition": {
    "enable": true,           // Defaulted to "false" with a tsconfig. Enables better IntelliSense in JS.
    "include": [ "jquery" ],  // Specific libs to fetch .d.ts files that weren't picked up by ATA 
    "exclude": [ "node" ]     // Specific libs to not fetch .d.ts files for
  }
}
```

## <a name="example-project-configuration"></a>Exemple de configuration de projet

Pour un projet donné avec la configuration suivante :
- Les fichiers sources du projet sont dans `wwwroot/js`
- Les fichiers lib du projet sont dans `wwwrrot/lib`
- `bootstrap`, `jquery`, `jquery-validation` et `jquery-validation-unobtrusive` sont répertoriés dans `bower.json`
- `kendo-ui` a été ajouté manuellement au dossier lib

![Structure des dossiers](./media/folderStructure.png)

Vous pouvez utiliser le fichier `tsconfig.json` suivant pour vérifier, d’une part, que le service de langage analyse uniquement vos fichiers sources dans le dossier `js` et, d’autre part, qu’il récupère et utilise toujours les fichiers `.d.ts` pour les bibliothèques dans votre dossier `lib`.

```json
{
  "compilerOptions": {
    "allowJs": true,          
    "noEmit": true            
  },
  "exclude": ["wwwroot/lib"],  //ignore lib folders, we will get IntelliSense via ATA
  "typeAcquisition": {
    "enable": true,            
    "include": [ "kendo-ui" ]  //kendo-ui wasn't added via bower, so we need to list it here
  }
}
```

# <a name="notable-changes-from-vs-2015"></a>Changements notables par rapport à VS 2015 
[!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] propose un tout nouveau service de langage : certains comportements ont disparu, tandis que d’autres comportements sont différents de ceux de l’expérience précédente.
Le remplacement de VSDoc par JSDoc, la suppression des extensions `.intellisense.js` personnalisées et la limitation d’IntelliSense pour des modèles de code spécifiques constituent les changements les plus importants.

## <a name="no-more-references-or-referencesjs"></a>Disparition de `///<references/>` et de `_references.js`
Par le passé, il était assez difficile de savoir quels fichiers figuraient dans votre portée IntelliSense à un moment donné.
Selon les cas, il était préférable ou non d’avoir tous les fichiers dans la portée. Il en résultait des configurations complexes qui nécessitaient la gestion manuelle des références.
Dorénavant, vous n’avez plus besoin de vous soucier de la gestion des références et vous n’êtes plus obligé d’utiliser des commentaires pour les références à trois barres obliques ou des fichiers `_references.js`.

Pour plus d’informations sur le fonctionnement d’IntelliSense, consultez la page [JavaScript IntelliSense](/visualstudio/ide/javascript-intellisense/).

## <a name="vsdoc"></a>VSDoc
Avant, vous pouviez utiliser des commentaires de documentation XML, appelés parfois VSDocs, pour décorer votre code source avec des données supplémentaires utilisées pour enrichir les résultats d’IntelliSense.
VSDoc n’est plus pris en charge. Il est désormais remplacé par [JSDoc](http://usejsdoc.org/about-getting-started.html), standard accepté pour JavaScript, qui est plus facile à écrire.

### <a name="intellisensejs-extensions"></a>Extensions `.intellisense.js`
Vous pouviez auparavant créer des [extensions IntelliSense](https://msdn.microsoft.com/en-us/library/hh874692.aspx) pour ajouter des résultats de saisie semi-automatique personnalisés pour des bibliothèques tierces.
Ces extensions étaient assez difficiles à écrire, et leur installation et leur référencement étaient peu pratiques. Le nouveau service de langage ne prend donc plus en charge ces fichiers.
Une autre méthode plus simple consiste à écrire un fichier de définition TypeScript pour offrir les mêmes fonctionnalités IntelliSense que les anciennes extensions `.intellisense.js`.
Pour en savoir plus sur la création de fichiers de déclaration (`.d.ts`), cliquez [ici](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html).

### <a name="unsupported-patterns"></a>Modèles non pris en charge
Étant donné que le nouveau service de langage repose sur l’analyse statique et non sur un moteur d’exécution (pour plus d’informations sur les différences, lisez [ce problème](https://github.com/Microsoft/TypeScript/issues/4789)), quelques modèles JavaScript ne peuvent plus être détectés.
Le modèle le plus courant est le modèle « expando ». Le service de langage ne peut pas fournir la fonctionnalité IntelliSense sur des objets auxquels des propriétés ont été ajoutées après la déclaration.
Exemple :

```js
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense won't show properties a or b
```

Vous pouvez contourner ce problème en déclarant les propriétés durant la création des objets :
```js
var obj = {
    "a": 10,
    "b": "hello world"
}
obj. // IntelliSense shows properties a and b
```

Vous pouvez également ajouter un commentaire JSDoc comme indiqué ci-dessus :
```js
/**
 * @type {{a: number, b: string}}
 */
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense shows properties a and b
```