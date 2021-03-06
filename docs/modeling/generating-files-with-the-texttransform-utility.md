---
title: "Génération de fichiers avec l’utilitaire TextTransform | Documents Microsoft"
ms.custom: 
ms.date: 09/21/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: "41"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 1d168695aca3626fa1ba351aef56faf001c5b6ee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="generating-files-with-the-texttransform-utility"></a>Génération de fichiers avec l'utilitaire TextTransform
TextTransform.exe est un outil de ligne de commande que vous pouvez utiliser pour transformer un modèle de texte. Lorsque vous appelez TextTransform.exe, vous spécifiez le nom d’un fichier de modèle de texte en tant qu’argument. TextTransform.exe appelle le moteur de transformation de texte et traite le modèle de texte. TextTransform.exe est généralement appelée à partir de scripts. Toutefois, il n’est pas généralement requis, car vous pouvez effectuer une transformation de texte dans Visual Studio ou dans le processus de génération.  
  
> [!NOTE]
>  Si vous souhaitez effectuer une transformation de texte dans le cadre du processus de génération, envisagez d’utiliser la tâche de transformation de texte de MSBuild. Pour plus d’informations, consultez [génération de Code dans un processus de génération](../modeling/code-generation-in-a-build-process.md). Dans un ordinateur sur lequel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est installé, vous pouvez également écrire une application ou [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Extension qui peut transformer des modèles de texte. Pour plus d’informations, consultez [le traitement des modèles de texte à l’aide d’un hôte personnalisé](../modeling/processing-text-templates-by-using-a-custom-host.md).  
  
 TextTransform.exe se trouve dans le répertoire suivant :  
  
 **\Program fichiers (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**  

pour l’édition Professional, ou

 **\Program fichiers (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE**
 
 pour l’édition Enterprise.

Dans les versions précédentes de Visual Studio, le fichier se trouve à l’emplacement suivant :

**\Program fichiers (x86) \Common Files\Microsoft Shared\TextTemplating\{version}**

où {version} dépend de la version précédente est installée.

## <a name="syntax"></a>Syntaxe  
  
```  
TextTransform [<options>] <templateName>  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|**Argument**|**Description**|  
|------------------|---------------------|  
|`templateName`|Identifie le nom du fichier de modèle que vous souhaitez transformer.|  
  
|**Option**|**Description**|  
|----------------|---------------------|  
|**-out** \<nom de fichier >|Le fichier dans lequel la sortie de la transformation est écrite.|  
|**r -** \<assembly >|Un assembly utilisé pour la compilation et l’exécution du modèle de texte.|  
|**-u** \<espace de noms >|Un espace de noms qui est utilisée pour compiler le modèle.|  
|**-I** \<includedirectory >|Un répertoire qui contient les modèles de texte inclus dans le modèle de texte spécifié.|  
|**P -** \<referencepath >|Un répertoire pour rechercher des assemblys spécifié dans le modèle de texte ou à l’aide de la **- r** option.<br /><br /> Par exemple, pour inclure les assemblys utilisés pour l’API Visual Studio, utilisez :<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|  
|**le point de distribution -** \<processorName > !\< className > ! \<assemblyName &#124; codeBase >|Nom, nom de type complet et assembly d’un processeur de directive peut être utilisé pour traiter des directives personnalisées dans le modèle de texte.|  
|**-un** [processorName] ! [ directiveName] ! \<nom_paramètre > ! \<parameterValue >|Spécifiez une valeur de paramètre pour un processeur de directive. Si vous spécifiez simplement le nom de paramètre et la valeur, le paramètre sera disponible pour tous les processeurs de directive. Si vous spécifiez un processeur de directive, le paramètre est disponible uniquement pour le processeur est spécifié. Si vous spécifiez un nom de directive, le paramètre est disponible uniquement lorsque la directive spécifiée est en cours de traitement.<br /><br /> Pour accéder aux valeurs de paramètre à partir d’un processeur de directive ou d’un modèle de texte, utilisez <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost.ResolveParameterValue%2A>. Dans un modèle de texte, incluez `hostspecific` dans la directive de modèle et d’appeler le message sur `this.Host`. Exemple :<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Entrez toujours le ' !' marque, même si vous omettez le processeur et les noms de directive. Exemple :<br /><br /> `-a !!param!value`|  
|**-h**|Fournit une aide.|  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Tâche|Rubrique|  
|----------|-----------|  
|Générer des fichiers dans une solution [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|[Génération de code au moment du design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|  
|Écrire des processeurs de directive pour transformer vos propres sources de données.|[Personnalisation d’une transformation de texte T4](../modeling/customizing-t4-text-transformation.md)|  
|Écrivez un hôte de création de modèles de texte qui vous permet d’appeler des modèles de texte à partir de votre propre application.|[Traitement des modèles de texte à l’aide d’un hôte personnalisé](../modeling/processing-text-templates-by-using-a-custom-host.md)|
