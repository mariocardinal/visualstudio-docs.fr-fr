---
title: Guide pratique pour fractionner une classe en classes partielles (Concepteur de classes) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7ae5781c965c4c80dcb592d8638408b109fd60d7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-split-a-class-into-partial-classes-class-designer"></a>Comment : fractionner une classe en classes partielles (Concepteur de classes)
Vous pouvez diviser la déclaration d’une classe ou d’une structure en plusieurs déclarations à l’aide du mot clé `Partial` en Visual Basic ou du mot clé `partial` en Visual C#. Vous pouvez utiliser autant de déclarations partielles que vous le souhaitez, dans autant de fichiers sources que vous le souhaitez ou dans un même fichier source. Toutefois, toutes les déclarations doivent être dans le même assembly et le même espace de noms.  
  
 Les classes partielles sont utiles dans plusieurs situations. Par exemple, lorsque vous travaillez sur de grands projets, le fait de séparer une classe en plusieurs fichiers permet à plusieurs programmeurs de travailler dessus en même temps. Lorsque vous utilisez du code généré par Visual Studio, vous pouvez modifier la classe sans avoir à recréer le fichier source. Le code Windows Forms et le code wrapper de service web sont des exemples de code généré par Visual Studio. Vous pouvez donc écrire du code qui utilise des classes autogénérées sans avoir à modifier le fichier créé par Visual Studio.  
  
 Il existe deux types de méthodes partielles. En Visual C#, on parle de méthodes déclarantes et implémentantes. En Visual Basic, on parle de méthodes de déclaration et d’implémentation.  
  
 Le Concepteur de classes prend en charge les classes et les méthodes partielles. La forme de type du diagramme de classes fait référence à un emplacement de déclaration unique de la classe partielle. Si la classe partielle est définie dans plusieurs fichiers, vous pouvez spécifier quel emplacement de déclaration le Concepteur de classes utilisera en définissant la propriété **Nouvel emplacement de membre** dans la fenêtre **Propriétés**. Autrement dit, lorsque vous double-cliquez sur une forme de classe, le Concepteur de classes accède au fichier source qui contient la déclaration de classe identifiée par la propriété **Nouvel emplacement de membre**. Lorsque vous double-cliquez sur une méthode partielle dans une forme de classe, le Concepteur de classes accède à la déclaration de méthode partielle. En outre, dans la fenêtre **Propriétés**, la propriété **Nom de fichier** référence l’emplacement de la déclaration. Pour les classes partielles, la propriété **Nom de fichier** répertorie tous les fichiers qui contiennent du code de déclaration et d’implémentation pour cette classe. Toutefois, pour les méthodes partielles, la propriété **Nom de fichier** répertorie uniquement le fichier qui contient la déclaration de méthode partielle.  
  
 L’exemple suivant fractionne la définition de la classe `Employee` en deux déclarations, dont chacune définit une procédure différente. Les deux définitions partielles des exemples peuvent se trouver dans le même fichier source ou dans deux fichiers sources différents.  
  
> [!NOTE]
>  Visual Basic utilise des définitions de classe partielle pour séparer le code généré par Visual Studio du code créé par l’utilisateur. Le code est réparti dans des fichiers sources distincts. Par exemple, le **Concepteur Windows Form** définit des classes partielles pour des contrôles tels que `Form`. Vous ne devez pas modifier le code généré dans ces contrôles.  
  
 Pour plus d’informations sur les types partiels en Visual Basic, consultez [Partiel](/dotnet/visual-basic/language-reference/modifiers/partial).  
  
## <a name="example"></a>Exemple  
 Pour fractionner une définition de classe en Visual Basic, utilisez le mot clé `Partial`, comme indiqué dans l’exemple suivant.  
  
```vb  
' First part of class definition.  
Partial Public Class Employee  
    Public Sub CalculateWorkHours()  
    End Sub  
End Class  
  
' Second part of class definition.  
Partial Public Class Employee  
    Public Sub CalculateTaxes()  
    End Sub  
End Class  
```  
  
## <a name="example"></a>Exemple  
 Pour fractionner une définition de classe en Visual C#, utilisez le mot clé `partial`, comme indiqué dans l’exemple suivant.  
  
```csharp  
// First part of class definition.  
public partial class Employee  
{  
    public void CalculateWorkHours()  
    {  
    }  
}  
  
// Second part of class definition.  
public partial class Employee  
{  
    public void CalculateTaxes()  
    {  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Classes et méthodes partielles](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [partial (type)](/dotnet/csharp/language-reference/keywords/partial-type)   
 [partielle, méthode (Référence C#)](/dotnet/csharp/language-reference/keywords/partial-method)   
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)