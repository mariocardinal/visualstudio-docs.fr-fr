---
title: "T4 Directive du modèle | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b0a8e04-6fee-4c6c-b086-e49fc728a3ed
caps.latest.revision: 10
author: alancameronwills
ms.author: awills
manager: douge
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
translationtype: Machine Translation
ms.sourcegitcommit: eb2ab9d49cdeb1ed71da8ef67841f7796862dc30
ms.openlocfilehash: ae369eacf934db165a10783bb59ad8a812f8c542
ms.lasthandoff: 02/22/2017

---
# <a name="t4-template-directive"></a>Directive du modèle T4
En général, un modèle de texte T4 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] commence par une directive `template`, qui spécifie comment le modèle doit être traité. Il ne doit y avoir qu'une seule directive de modèle dans un modèle de texte et les fichiers qu'il contient.  
  
 Pour obtenir une vue d’ensemble de l’écriture de modèles de texte, consultez [écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md).  
  
## <a name="using-the-template-directive"></a>Utilisation de la directive du modèle  
  
```  
<#@ template [language="VB"] [compilerOptions="options"] [culture="code"] [debug="true"] [hostspecific="true"] [inherits="templateBaseClass"] [visibility="internal"] [linePragmas="false"] #>  
```  
  
 La directive `template` comporte plusieurs attributs qui vous permettent de spécifier différents aspects de la transformation. Tous les attributs sont facultatifs.  
  
## <a name="compileroptions-attribute"></a>attribut compilerOptions  
 Exemple :  
 `compilerOptions="optimize+"`  
  
 Valeurs valides :  
 Toutes les options du compilateur valides.  
  
 Ignoré pour les modèles au moment de l'exécution (prétraités).  
  
 Ces options sont appliquées lorsque le modèle a été converti en [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)], et que le code résultant est compilé.  
  
## <a name="culture-attribute"></a>attribut de culture  
 Exemple :  
 `culture="de-CH"`  
  
 Valeurs valides :  
 "", la culture dite indifférente, qui est la valeur par défaut.  
  
 Culture exprimée sous la forme d'une chaîne au format xx-XX. Par exemple, en-US, ja-JP, de-CH, de-DE. Pour plus d’informations, consultez <xref:System.Globalization.CultureInfo?displayProperty=fullName>.</xref:System.Globalization.CultureInfo?displayProperty=fullName>  
  
 L'attribut de culture spécifie la culture à utiliser lorsqu'un bloc d'expression est converti en texte.  
  
## <a name="debug-attribute"></a>attribut de débogage  
 Exemple :  
 ```  
debug="true"  
```  
  
 Valeurs valides :  
 `true, false`. False représente la valeur par défaut.  
  
 Si l'attribut `debug` a la valeur `true`, le fichier de code intermédiaire contient des informations qui permettent au débogueur d'identifier plus précisément la position, dans votre modèle, où s'est produit un arrêt ou une exception.  
  
 Pour les modèles de conception le fichier de code intermédiaire est écrit pour votre **%temp%** active.  
  
 Pour exécuter un modèle au moment du design dans le débogueur, enregistrez le modèle de texte, puis ouvrez le menu contextuel du modèle de texte dans l’Explorateur de solutions et choisissez **déboguer le modèle T4**.  
  
## <a name="hostspecific-attribute"></a>attribut hostspecific  
 Exemple :  
 ```  
hostspecific="true"  
```  
  
 Valeurs valides :  
 `true, false, trueFromBase`. False représente la valeur par défaut.  
  
 Si vous affectez à cet attribut la valeur `true`, une propriété nommée `Host` est ajoutée à la classe générée par votre modèle de texte. La propriété est une référence à l’hôte du moteur de transformation et est déclarée comme <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>.</xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> Si vous avez défini un hôte personnalisé, vous pouvez effectuer un cast de celui-ci en type d'hôte personnalisé.  
  
 Étant donné que le type de cette propriété dépend du type d'hôte, elle n'est utile que si vous écrivez un modèle de texte qui fonctionne uniquement avec un hôte spécifique. Cela s’applique aux [les modèles au moment du design](../modeling/design-time-code-generation-by-using-t4-text-templates.md), mais pas [modèles au moment de l’exécution](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Lorsque `hostspecific` a la valeur `true` et que vous utilisez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous pouvez effectuer un cast de `this.Host` en IServiceProvider pour accéder aux fonctionnalités de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Vous pouvez également utiliser `Host.ResolvePath(filename)` pour obtenir le chemin d'accès absolu d'un fichier dans le projet. Exemple :  
  
```c#  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="EnvDTE" #>  
<#@ import namespace="System.IO" #>  
<# // Get the Visual Studio API as a service:  
 DTE dte = ((IServiceProvider)this.Host).GetCOMService(typeof(DTE)) as DTE;    
#>  
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>  
  
<#  
 // Find a path within the current project:  
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));  
#>  
Content of myFile is:  
<#= myFile #>  
  
```  
  
 Si vous utilisez les attributs `inherits` et `hostspecific` ensemble, spécifiez host="trueFromBase" dans la classe dérivée et host="true" dans la classe de base. Cela évite une double définition de la propriété `Host` dans le code généré.  
  
## <a name="language-attribute"></a>attribut de langage  
 Exemple :  
 `language="VB"`  
  
 Valeurs valides :  
 `C#` (par défaut)  
  
 `VB`  
  
 L’attribut de langage spécifie le langage ([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]) à utiliser pour le code source dans les blocs d’instruction et d’expression. Le fichier de code intermédiaire à partir duquel la sortie est générée utilisera ce langage. Ce langage n'est pas lié au langage que votre modèle génère, qui peut être tout type de texte.  
  
 Exemple :  
  
```vb#  
<#@ template language="VB" #>  
<#@ output extension=".txt" #>  
Squares of numbers:  
<#  
  Dim number As Integer  
  For number = 1 To 4  
#>  
  Square of <#= number #> is <#= number * number #>  
<#  
  Next number  
#>  
  
```  
  
## <a name="inherits-attribute"></a>attribut Inherits  
 Vous pouvez spécifier que le code du programme de votre modèle peut hériter d'une autre classe, qui peut également être générée à partir d'un modèle de texte.  
  
### <a name="inheritance-in-a-run-time-preprocessed-text-template"></a>Héritage dans un modèle de texte au moment de l'exécution (prétraité)  
 Vous pouvez utiliser l'héritage entre les modèles de texte au moment de l'exécution pour créer un modèle de base avec plusieurs variantes dérivées. Modèles d’exécution sont celles qui ont le **un outil personnalisé** propriété **TextTemplatingFilePreprocessor**. Un modèle au moment de l'exécution génère du code que vous pouvez appeler dans votre application pour créer le texte défini dans le modèle. Pour plus d’informations, consultez [génération de texte d’exécution avec les modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Si vous ne spécifiez pas d'attribut `inherits`, une classe de base et une classe dérivée sont générées à partir de votre modèle de texte. Lorsque vous spécifiez un attribut `inherits`, seule la classe dérivée est générée. Vous pouvez écrire une classe de base manuellement, mais elle doit fournir les méthodes utilisées par la classe dérivée.  
  
 Plus généralement, vous spécifiez un autre modèle prétraité comme classe de base. Le modèle de base fournit des blocs de texte communs, qui peuvent être entrelacés avec du texte des modèles dérivés. Vous pouvez utiliser des blocs de fonctionnalité de classe `<#+ ... #>` pour définir des méthodes qui contiennent des fragments de texte. Par exemple, vous pouvez placer l'infrastructure du texte de sortie dans le modèle de base, en fournissant des méthodes virtuelles qui peuvent être substituées dans les modèles dérivés :  
  
 Modèle de texte au moment de l'exécution (prétraité) BaseTemplate.tt :  
 ```scr  
This is the common header.  
<#   
  SpecificFragment1();   
#>  
A common central text.  
<#   
  SpecificFragment2();   
#>  
This is the common footer.  
<#+   
  // Declare abstract methods  
  protected virtual void SpecificFragment1() { }  
  protected virtual void SpecificFragment2() { }  
#>  
  
```  
  
 Modèle de texte au moment de l'exécution (prétraité) DerivedTemplate1.tt :  
 ```c#  
<#@ template language="C#" inherits="BaseTemplate" #>  
<#   
  // Run the base template:  
  base.TransformText();  
#>  
<#+  
// Provide fragments specific to this derived template:  
protected override void SpecificFragment1()  
{  
#>  
   Fragment 1 for DerivedTemplate1  
<#+  
}  
protected override void SpecificFragment2()  
{  
#>  
   Fragment 2 for DerivedTemplate1  
<#+  
}  
#>  
  
```  
  
 Code d'application pour appeler DerivedTemplate1 :  
 ```c#  
Console.WriteLine(new DerivedTemplate().TransformText());  
```  
  
 Résultat :  
 ```  
This is the common header.  
   Fragment 1 for DerivedTemplate1  
A common central text.  
   Fragment 2 for DerivedTemplate1  
This is the common footer.  
```  
  
 Vous pouvez générer les classes de base et les classes dérivées dans des projets différents. Pensez à ajouter l'assembly ou le projet de base aux références du projet dérivé.  
  
 Vous pouvez également utiliser une classe écrite manuellement ordinaire comme classe de base. La classe de base doit fournir les méthodes utilisées par la classe dérivée.  
  
> [!WARNING]
>  Si vous utilisez les attributs `inherits` et `hostspecific` ensemble, spécifiez hostspecific="trueFromBase" dans la classe dérivée et host="true" dans la classe de base. Cela évite une double définition de la propriété `Host` dans le code généré.  
  
### <a name="inheritance-in-a-design-time-text-template"></a>Héritage dans un modèle de texte au moment du design  
 Un modèle de texte au moment du design est un fichier pour lequel **un outil personnalisé** a **TextTemplatingFileGenerator**. Le modèle génère un fichier de sortie de code ou de texte, qui fait partie de votre projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pour générer le fichier de sortie, le modèle est d'abord traduit en fichier de code du programme intermédiaire, que vous ne voyez normalement pas. L'attribut `inherits` spécifie la classe de base pour ce code intermédiaire.  
  
 Pour un modèle de texte au moment du design, vous pouvez spécifier toute classe de base qui est dérivée de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>.</xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> Utilisez la directive `<#@assembly#>` pour charger l'assembly ou le projet qui contient la classe de base.  
  
 Pour plus d’informations, consultez [« Héritage de modèles de texte » dans le Blog de Gareth Jones](http://go.microsoft.com/fwlink/?LinkId=208373).  
  
## <a name="linepragmas-attribute"></a>Attribut LinePragmas  
 Exemple :  
 `linePragmas="false"`  
  
 Valeurs valides :  
 `true` (par défaut)  
  
 `false`  
  
 L’assignation de la valeur false à cet attribut permet de supprimer les étiquettes qui identifient les numéros de ligne dans le code généré. Cela signifie que le compilateur signale toutes les erreurs en utilisant les numéros de ligne du code généré. Cela vous donne davantage d'options de débogage, car vous pouvez choisir de déboguer le modèle de texte ou le code généré.  
  
 Cet attribut peut aussi être utile si vous remarquez que les noms de fichiers absolus dans les pragmas entraînent des problèmes de fusion sous contrôle de code source.  
  
## <a name="visibility-attribute"></a>Attribut Visibility  
 Exemple :  
 `visibility="internal"`  
  
 Valeurs valides :  
 `public` (par défaut)  
  
 `internal`  
  
 Dans un modèle de texte au moment de l'exécution, vous définissez l'attribut de visibilité de la classe générée. Par défaut, la classe fait partie de l'API publique de votre code, mais en définissant `visibility="internal"`, vous pouvez vous assurer que votre code est en mesure d'utiliser la classe de génération de texte.
