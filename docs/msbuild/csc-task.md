---
title: "Csc, tâche | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Csc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Csc task [MSBuild]
- MSBuild, Csc task
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
caps.latest.revision: 26
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
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: 9057a6bd209d4761c147577888dffa2933bbf4c8
ms.lasthandoff: 02/22/2017

---
# <a name="csc-task"></a>Csc, tâche
Encapsule CSC.exe et produit des fichiers exécutables (.exe), des bibliothèques de liens dynamiques (.dll) ou des modules de code (.netmodule). Pour plus d’informations sur CSC.exe, consultez l’article [C# Compiler Options (Options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/index).  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `Csc`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Paramètre `String[]` facultatif.<br /><br /> Spécifie des répertoires supplémentaires dans lesquels rechercher des références. Pour plus d’informations, consultez l’article [/lib (C# Compiler Options) (/lib [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option).|  
|`AddModules`|Paramètre `String` facultatif.<br /><br /> Spécifie un ou plusieurs modules à inclure dans cet assembly. Pour plus d’informations, consultez l’article [/addmodule (C# Compiler Options) (/addmodule [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option).|  
|`AllowUnsafeBlocks`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, compile le code qui utilise le mot clé [unsafe](/dotnet/csharp/language-reference/keywords/unsafe). Pour plus d’informations, consultez l’article [/unsafe (C# Compiler Options) (/unsafe [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).|  
|`ApplicationConfiguration`|Paramètre `String` facultatif.<br /><br /> Spécifie le fichier de configuration de l’application contenant les paramètres de liaison d’assembly.|  
|`BaseAddress`|Paramètre `String` facultatif.<br /><br /> Spécifie l'adresse de base préférée à laquelle charger une DLL. L’adresse de base par défaut d’une DLL est définie par le common language runtime [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Pour plus d’informations, consultez l’article [/baseaddress (C# Compiler Options) (/baseaddress [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).|  
|`CheckForOverflowUnderflow`|Paramètre `Boolean` facultatif.<br /><br /> Indique si l’arithmétique sur les entiers qui dépasse les limites du type de données entraîne une exception au moment de l’exécution. Pour plus d’informations, consultez l’article [/checked (C# Compiler Options) (/checked [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).|  
|`CodePage`|Paramètre `Int32` facultatif.<br /><br /> Spécifie la page de codes à utiliser pour tous les fichiers de code source inclus dans la compilation. Pour plus d’informations, consultez l’article [/codepage (C# Compiler Options) (/codepage [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option).|  
|`DebugType`|Paramètre `String` facultatif.<br /><br /> Spécifie le type de débogage. `DebugType` peut avoir la valeur `full` ou `pdbonly`. La valeur par défaut est `full`, ce qui permet d’attacher un débogueur à un programme en cours d’exécution. La spécification de `pdbonly` active le débogage du code source lorsque le programme est démarré dans le débogueur, mais affiche uniquement un assembleur lorsque le programme en cours d’exécution est attaché au débogueur.<br /><br /> Ce paramètre remplace le paramètre `EmitDebugInformation`.<br /><br /> Pour plus d’informations, consultez l’article [/debug (C# Compiler Options) (/debug [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).|  
|`DefineConstants`|Paramètre `String` facultatif.<br /><br /> Définit les symboles du préprocesseur. Pour plus d’informations, consultez l’article [/define (C# Compiler Options) (/define [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).|  
|`DelaySign`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, indique que vous souhaitez obtenir un assembly complètement signé. Si `false`, indique que vous souhaitez placer uniquement la clé publique dans l’assembly.<br /><br /> Ce paramètre n’a aucun effet, sauf s’il est utilisé avec les paramètres `KeyFile` ou `KeyContainer`.<br /><br /> Pour plus d’informations, consultez l’article [/delaysign (C# Compiler Options) (/delaysign [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option).|  
|`DisabledWarnings`|Paramètre `String` facultatif.<br /><br /> Spécifie la liste d’avertissements à désactiver. Pour plus d’informations, consultez l’article [/nowarn (C# Compiler Options) (/nowarn [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).|  
|`DocumentationFile`|Paramètre `String` facultatif.<br /><br /> Traite les commentaires de documentation pour les diriger vers un fichier XML. Pour plus d’informations, consultez l’article [/doc (C# Compiler Options) (/doc [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).|  
|`EmitDebugInformation`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, la tâche génère des informations de débogage et les place dans un fichier de base de données du programme (.pdb). Si `false`, la tâche n’émet aucune information de débogage. La valeur par défaut est `false`. Pour plus d’informations, consultez l’article [/debug (C# Compiler Options) (/debug [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).|  
|`ErrorReport`|Paramètre `String` facultatif.<br /><br /> Fournit un moyen pratique de signaler une erreur interne C# à Microsoft. Ce paramètre peut avoir la valeur `prompt`, `send` ou `none`. Si le paramètre est défini sur `prompt`, vous recevez une invite lorsqu’une erreur interne du compilateur se produit. Cette invite vous permet d’envoyer un rapport de bogue par voie électronique à Microsoft. Si le paramètre est défini sur `send`, un rapport de bogue est automatiquement envoyé. Si le paramètre est défini sur `none`, l’erreur est signalée uniquement dans la sortie de texte du compilateur. La valeur par défaut est `none`. Pour plus d’informations, consultez l’article [/errorreport (C# Compiler Options) (/errorreport [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).|  
|`FileAlignment`|Paramètre `Int32` facultatif.<br /><br /> Spécifie la taille des sections dans le fichier de sortie. Pour plus d’informations, consultez l’article [/filealign (C# Compiler Options) (/filealign [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).|  
|`GenerateFullPaths`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, spécifie le chemin d’accès absolu au fichier dans la sortie du compilateur. Si `false`, spécifie le nom du fichier. La valeur par défaut est `false`. Pour plus d’informations, consultez l’article [/fullpaths (C# Compiler Options) (/fullpaths [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option).|  
|`KeyContainer`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom du conteneur de la clé de chiffrement. Pour plus d’informations, consultez l’article [/keycontainer (C# Compiler Options) (/keycontainer [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option).|  
|`KeyFile`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom du fichier contenant la clé de chiffrement. Pour plus d’informations, consultez l’article [/keyfile (C# Compiler Options) (/keyfile [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option).|  
|`LangVersion`|Paramètre `String` facultatif.<br /><br /> Spécifie la version du langage à utiliser. Pour plus d’informations, consultez l’article [/langversion (C# Compiler Options) (/langversion [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).|  
|`LinkResources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Crée un lien à une ressource [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] dans le fichier de sortie ; le fichier de ressources n’est pas placé dans le fichier de sortie.<br /><br /> Les éléments transmis dans ce paramètre peuvent posséder des entrées de métadonnées facultatives nommées `LogicalName` et `Access`. `LogicalName` correspond au paramètre `identifier` du commutateur `/linkresource`, et `Access` correspond au paramètre `accessibility-modifier`. Pour plus d’informations, consultez l’article [/linkresource (C# Compiler Options) (/linkresource [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option).|  
|`MainEntryPoint`|Paramètre `String` facultatif.<br /><br /> Spécifie l’emplacement de la méthode `Main`. Pour plus d’informations, consultez l’article [/main (C# Compiler Options) (/main [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/main-compiler-option).|  
|`ModuleAssemblyName`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom de l’assembly dont ce module doit faire partie.|  
|`NoConfig`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, indique au compilateur de ne pas compiler avec le fichier csc.rsp. Pour plus d’informations, consultez l’article [/noconfig (C# Compiler Options) (/noconfig [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option).|  
|`NoLogo`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, supprime l’affichage des informations de bannière du compilateur. Pour plus d’informations, consultez l’article [/nologo (C# Compiler Options) (/nologo [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option).|  
|`NoStandardLib`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, empêche l’importation du fichier mscorlib.dll, qui définit l’espace de noms système tout entier. Utilisez ce paramètre si vous souhaitez définir ou créer vos propres objets et espace de noms système. Pour plus d’informations, consultez l’article [/nostdlib (C# Compiler Options) (/nostdlib [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).|  
|`NoWin32Manifest`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, n’inclut pas le manifeste Win32 par défaut.|  
|`Optimize`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, active les optimisations. Si `false`, désactive les optimisations. Pour plus d’informations, consultez l’article [/optimize (C# Compiler Options) (/optimize [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).|  
|`OutputAssembly`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie le nom du fichier de sortie. Pour plus d’informations, consultez l’article [/out (C# Compiler Options) (/out [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/out-compiler-option).|  
|`PdbFile`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom de fichier des informations de débogage. Le nom par défaut est le nom de fichier de sortie pourvu d’une extension .pdb.|  
|`Platform`|Paramètre `String` facultatif.<br /><br /> Spécifie la plateforme de processeur ciblée par le fichier de sortie. Ce paramètre peut avoir la valeur `x86`, `x64` ou `anycpu`. La valeur par défaut est `anycpu`. Pour plus d’informations, consultez l’article [/platform (C# Compiler Options) (/platform [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).|  
|`References`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Provoque l’importation par la tâche des informations de type public dans le projet actuel à partir des éléments spécifiés. Pour plus d’informations, consultez l’article [/reference (C# Compiler Options) (/reference [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Vous pouvez spécifier un alias de référence [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] dans un fichier [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] en ajoutant les métadonnées `Aliases` à l’élément « Reference » d’origine. Par exemple, pour définir l’alias « LS1 » dans la ligne de commande CSC suivante :<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> Vous devez utiliser :<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Incorpore une ressource [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] dans le fichier de sortie.<br /><br /> Les éléments transmis dans ce paramètre peuvent posséder des entrées de métadonnées facultatives nommées `LogicalName` et `Access`. `LogicalName` correspond au paramètre `identifier` du commutateur `/resource`, et `Access` correspond au paramètre `accessibility-modifier`. Pour plus d’informations, consultez l’article [/resource (C# Compiler Options) (/resource [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option).|  
|`ResponseFiles`|Paramètre `String` facultatif.<br /><br /> Spécifie le fichier réponse qui contient les commandes correspondant à cette tâche. Pour plus d’informations, consultez [@ (Spécifier un fichier réponse)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option).|  
|`Sources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie un ou plusieurs fichiers sources [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].|  
|`TargetType`|Paramètre `String` facultatif.<br /><br /> Spécifie le format de fichier du fichier de sortie. Ce paramètre peut avoir la valeur `library`, qui crée une bibliothèque de codes, `exe`, qui crée une application console, `module`, qui crée un module, ou `winexe`, qui crée un programme Windows. La valeur par défaut est `library`. Pour plus d’informations, consultez l’article [/target (C# Compiler Options) (/target [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/target-compiler-option).|  
|`TreatWarningsAsErrors`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, traite tous les avertissements comme des erreurs. Pour plus d’informations, consultez l’article [/warnaserror (C# Compiler Options) (/warnaserror [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).|  
|`UseHostCompilerIfAvailable`|Paramètre `Boolean` facultatif.<br /><br /> Demande à la tâche d’utiliser l’objet de compilateur in-process s’il est disponible. Son utilisation est réservée à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|`Utf8Output`|Paramètre `Boolean` facultatif.<br /><br /> Enregistre les résultats de la compilation au format d’encodage UTF-8. Pour plus d’informations, consultez l’article [/utf8output (C# Compiler Options) (/utf8output [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option).|  
|`WarningLevel`|Paramètre `Int32` facultatif.<br /><br /> Spécifie le niveau d’avertissement que le compilateur doit afficher. Pour plus d’informations, consultez l’article [/warn (C# Compiler Options) (/warn [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).|  
|`WarningsAsErrors`|Paramètre `String` facultatif.<br /><br /> Spécifie une liste d'avertissements à traiter comme des erreurs. Pour plus d’informations, consultez l’article [/warnaserror (C# Compiler Options) (/warnaserror [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Ce paramètre remplace le paramètre `TreatWarningsAsErrors`.|  
|`WarningsNotAsErrors`|Paramètre `String` facultatif.<br /><br /> Spécifie une liste d'avertissements à ne pas traiter comme des erreurs. Pour plus d’informations, consultez l’article [/warnaserror (C# Compiler Options) (/warnaserror [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Ce paramètre est utile uniquement si le paramètre `TreatWarningsAsErrors` est défini sur `true`.|  
|`Win32Icon`|Paramètre `String` facultatif.<br /><br /> Insère un fichier .ico dans l’assembly, ce qui donne au fichier de sortie l’apparence souhaitée dans l’Explorateur de fichiers. Pour plus d’informations, consultez l’article [/win32icon (C# Compiler Options) (/win32icon [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option).|  
|`Win32Manifest`|Paramètre `String` facultatif.<br /><br /> Spécifie le manifeste Win32 à inclure.|  
|`Win32Resource`|Paramètre `String` facultatif.<br /><br /> Insère un fichier de ressources Win32 (.res) dans le fichier de sortie. Pour plus d’informations, consultez l’article [/win32res (C# Compiler Options) (/win32res [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option).|  
  
## <a name="remarks"></a>Notes  
 Outre les paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe `Microsoft.Build.Tasks.ManagedCompiler`, qui hérite de la classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, qui hérite elle-même de la classe <xref:Microsoft.Build.Utilities.ToolTask>. Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez l’article [ToolTaskExtension Base Class (Classe de base ToolTaskExtension)](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la tâche `Csc` pour compiler un fichier exécutable à partir des fichiers sources de la collection d’éléments `Compile`.  
  
```xml  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des tâches](../msbuild/msbuild-task-reference.md)   
 [Tâches](../msbuild/msbuild-tasks.md)
