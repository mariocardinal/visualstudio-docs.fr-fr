---
title: "Page Application, Concepteur de projet (C#) │ Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cs.ProjectPropertiesApplicationWPF
- cs.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
ms.assetid: f13701a8-4e2e-4474-9d60-bb43decbe0c1
caps.latest.revision: 56
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 6fbf89668d47d55d1d77a1d7f11765567fc73405
ms.openlocfilehash: 3f0056a62dc11c5584e38e9912ccd94f5b9e9b0e
ms.contentlocale: fr-fr
ms.lasthandoff: 05/26/2017

---
# <a name="application-page-project-designer-c"></a>Page Application, Concepteur de projet (C#)
Utilisez la page **Application** du **Concepteur de projet** pour spécifier les paramètres d’application et les propriétés du projet.  
  
 Pour accéder à la page **Application**, choisissez un nœud de projet (pas le nœud **Solution**) dans l’**Explorateur de solutions**. Ensuite, choisissez **Projet**, **Propriétés** dans la barre de menus. Quand le Concepteur de projet apparaît, cliquez sur l’onglet **Application**.  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="general-application-settings"></a>Paramètres d’application généraux  
 Les options suivantes permettent de configurer les paramètres généraux de l’application.  
  
 **Nom de l’assembly**  
 Spécifie le nom du fichier de sortie qui contient le manifeste de l’assembly. La modification de cette propriété modifie également la propriété **Nom de sortie**. Vous pouvez également effectuer cette modification à partir de la ligne de commande à l’aide de [/out (Options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option). Pour accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.  
  
 **Espace de noms par défaut**  
 Spécifie l’espace de noms de base pour les fichiers ajoutés au projet.  
  
 Consultez la rubrique [espace de noms](/dotnet/csharp/language-reference/keywords/namespace) pour plus d’informations sur la création d’espaces de noms dans votre code.  
  
 Pour accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.  
  
 **Framework cible**  
 Spécifie la version du .NET Framework ciblée par l’application. Cette option peut avoir des valeurs différentes selon les versions du .NET Framework installées sur votre ordinateur.  
  
 Par défaut, la valeur est la même que le framework cible que vous avez sélectionné dans la boîte de dialogue **Nouveau projet**.  
  
> [!NOTE]
>  Les packages de prérequis répertoriés dans la [boîte de dialogue Composants requis](../../ide/reference/prerequisites-dialog-box.md) sont définis automatiquement la première fois que vous ouvrez la boîte de dialogue. Si vous modifiez ultérieurement l'infrastructure cible du projet, vous devrez sélectionner manuellement les composants requis pour qu'ils correspondent à la nouvelle version cible de l'infrastructure.  
  
 Pour plus d’informations, consultez [Guide pratique pour cibler une version du .NET Framework](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) et [Présentation du multiciblage Visual Studio](../../ide/visual-studio-multi-targeting-overview.md).  
  
 **Type d’application**  
 Spécifie le type d’application à générer. Pour les applications [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)], vous pouvez spécifier **Application du Windows Store**, **Bibliothèque de classes** ou **Fichier WinMD**. Pour la plupart des autres types d’applications, vous pouvez spécifier **Application Windows**, **Application console**, **Bibliothèque de classes**, **Service Windows** ou **Bibliothèque de contrôles web**.  
  
 Pour un projet d’application web, vous devez spécifier **Bibliothèque de classes**.  
  
 Si vous spécifiez l’option **Fichier WinMD**, les types peuvent être projetés dans n’importe quel langage de programmation de Windows Runtime. En plaçant la sortie du projet dans un fichier WinMD, vous pouvez coder une application dans plusieurs langages et faire interagir le code comme si vous l’aviez écrit dans le même langage. Vous pouvez spécifier cette option pour les solutions qui ciblent les bibliothèques Windows Runtime, y compris les applications [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)]. Pour plus d’informations, consultez [Création de composants Windows Runtime en C# et Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).  
  
> [!NOTE]
>  Le Windows Runtime peut projeter des types pour qu’ils apparaissent comme des objets natifs dans le langage qui les utilise. Par exemple, les applications JavaScript qui interagissent avec Windows Runtime l’utilisent comme un ensemble d’objets JavaScript, et les applications C# utilisent la bibliothèque comme une collection d’objets .NET. En plaçant la sortie du projet dans un fichier WinMD, vous tirez parti de la même technologie que celle utilisée par Windows Runtime.  
  
 Pour plus d’informations sur la propriété **Type d’application**, consultez [/target (Options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option). Pour plus d’informations sur la façon d’accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.OutputType%2A>.  
  
 **Informations de l’assembly**  
 Cliquez sur ce bouton pour afficher la [boîte de dialogue Informations de l’assembly](../../ide/reference/assembly-information-dialog-box.md).  
  
 **Objet de démarrage**  
 Définit le point d’entrée à appeler quand l’application se charge. Cet objet est généralement défini sur le formulaire principal de votre application ou sur la procédure `Main` qui s’exécute quand l’application démarre. Comme les bibliothèques de classes n’ont pas de point d’entrée, la seule option disponible pour cette propriété est **(Non défini)**.  
  
 Par défaut, dans un projet d’application de navigateur WPF, cette option est **(Non défini)**. L’autre option est *nom_projet*.App. Dans ce type de projet, vous devez définir l’URI de démarrage pour charger une ressource d’interface utilisateur quand l’application démarre. Pour ce faire, ouvrez le fichier Application.xaml dans votre projet et définissez la propriété `StartupUri` sur un fichier .xaml dans votre projet, par exemple, Window1.xaml. Pour obtenir la liste des éléments racines valides, consultez <xref:System.Windows.Application.StartupUri%2A>. Vous devez également définir une méthode `public static void Main()` dans une classe du projet. Cette classe s’affiche dans la liste **Objet de démarrage** comme *nom_projet.nom_classe*. Vous pouvez ensuite sélectionner la classe comme objet de démarrage.  
  
 Pour plus d’informations, consultez [/main (Options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). Pour accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.StartupObject%2A>.  
  
## <a name="resources"></a>Ressources  
 Les options suivantes permettent de configurer les paramètres généraux de l’application.  
  
 **Icône et manifeste**  
 Par défaut, cette case d’option est sélectionnée et les options **Icône** et **Manifeste** sont activées. Cela vous permet de sélectionner votre propre icône ou différentes options de génération du manifeste. Laissez cette case d’option sélectionnée, sauf si vous fournissez un fichier de ressources pour le projet.  
  
 **Icône**  
 Définit le fichier .ico à utiliser comme icône de votre programme. Cliquez sur le bouton de sélection pour rechercher un graphique existant ou tapez le nom du fichier souhaité. Pour plus d’informations, consultez [/win32icon (Options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). Pour accéder à cette propriété par programmation, consultez <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.  
  
 **Manifest**  
 Sélectionne une option de génération de manifeste quand l’application s’exécute sur Windows Vista sous contrôle de compte d’utilisateur (UAC). Cette option peut avoir les valeurs suivantes :  
  
-   **Incorporer les paramètres par défaut dans le fichier manifeste**. Prend en charge le fonctionnement standard de Visual Studio sur Windows Vista, qui incorpore les informations de sécurité dans le fichier exécutable de l’application, en indiquant que `requestedExecutionLevel` doit être `AsInvoker`. Il s'agit de l'option par défaut.  
  
-   **Créer une application sans fichier manifeste**. Cette méthode est appelée *virtualisation*. Utilisez cette option pour la compatibilité avec les applications antérieures.  
  
-   **Propriétés\app.manifest**. Cette option est obligatoire pour les applications déployées par ClickOnce ou COM sans inscription. Si vous publiez une application à l’aide du déploiement ClickOnce, l’option **Manifeste** est automatiquement définie sur cette option.  
  
 **Fichier de ressources**  
 Sélectionnez cette case d’option, sauf si vous fournissez un fichier de ressources pour le projet. Cette option désactive les options **Icône** et **Manifeste**.  
  
 Entrez un nom de chemin ou utilisez le bouton Parcourir (**...** ) pour ajouter un fichier de ressources Win32 au projet.  
  
## <a name="see-also"></a>Voir aussi  
[Gestion des propriétés de l’application](../../ide/application-properties.md)  
 [Écriture de code dans les solutions Office](/office-dev/office-dev/writing-code-in-office-solutions)
