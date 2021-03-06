---
title: "Prise en charge de la barre de Navigation dans un Service de langage hérité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 935ea7d9fde2872c952f79afaa95058e9f18d0a7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Prise en charge de la barre de Navigation dans un Service de langage hérité
La barre de Navigation en haut de la vue de l’éditeur affiche les types et membres dans le fichier. Types sont affichés dans la liste déroulante gauche, et les membres sont affichés dans le droit de liste déroulante. Lorsque l’utilisateur sélectionne un type, le point d’insertion est placé sur la première ligne du type. Lorsque l’utilisateur sélectionne un membre, le point d’insertion est placé sur la définition du membre. Les zones de liste déroulante sont mis à jour pour refléter l’emplacement actuel du signe insertion.  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>Affichage et mise à jour de la barre de Navigation  
 Pour prendre en charge de la barre de Navigation, vous devez dériver une classe à partir de la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> classe et implémenter la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> (méthode). Lorsque votre service de langage est donnée à une fenêtre de code, la base de <xref:Microsoft.VisualStudio.Package.LanguageService> classe instancie le <xref:Microsoft.VisualStudio.Package.CodeWindowManager>, qui contient le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> objet représentant la fenêtre de code. Le <xref:Microsoft.VisualStudio.Package.CodeWindowManager> reçoit un nouvel objet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objet. Le <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> méthode obtient un <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objet. Si vous retournez une instance de votre <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> (classe), le <xref:Microsoft.VisualStudio.Package.CodeWindowManager> appelle votre <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> méthode pour remplir interne répertorie et passe votre <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> de l’objet à la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] déroulante barre manager. La liste déroulante barre manager, à son tour, appelle le <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> méthode sur votre <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objet pour établir le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> objet qui contient les deux barres de liste déroulante.  
  
 Lorsque le point d’insertion se déplace, le <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> les appels de méthode le <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> (méthode). La base de <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> les appels de méthode le <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> méthode dans votre <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> classe pour mettre à jour l’état de la barre de Navigation. Vous passez un jeu de <xref:Microsoft.VisualStudio.Package.DropDownMember> objets à cette méthode. Chaque objet représente une entrée dans la liste déroulante.  
  
## <a name="the-contents-of-the-navigation-bar"></a>Le contenu de la barre de Navigation  
 La barre de Navigation contient généralement une liste de types et une liste de membres. La liste des types inclut tous les types disponibles dans le fichier source actuel. Les noms de type incluent les informations de l’espace de noms complet. Voici un exemple de code c# avec deux types :  
  
```csharp  
namespace TestLanguagePackage  
{  
    public class TestLanguageService  
    {  
        internal struct Token  
        {  
            int tokenID;  
        }  
        private Tokens[] tokens;  
        private string serviceName;  
    }  
}  
```  
  
 Affiche la liste de type `TestLanguagePackage.TestLanguageService` et `TestLanguagePackage.TestLanguageService.Tokens`.  
  
 La liste des membres affiche les membres disponibles du type sélectionné dans la liste des types. À l’aide de l’exemple de code ci-dessus, si `TestLanguagePackage.TestLanguageService` est le type qui est sélectionné, la liste des membres contient les membres privés `tokens` et `serviceName`. La structure interne `Token` n’est pas affichée.  
  
 Vous pouvez implémenter la liste des membres pour afficher le nom d’un membre en gras lorsque le point d’insertion est placé à l’intérieur. Les membres peuvent également être affichés dans grisée de texte, indiquant qu’ils ne sont pas dans la portée où le point d’insertion est positionné.  
  
## <a name="enabling-support-for-the-navigation-bar"></a>L’activation de la prise en charge pour la barre de Navigation  
 Pour activer la prise en charge de la barre de Navigation, vous devez définir le `ShowDropdownBarOption` paramètre de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attribut `true`. Ce paramètre définit la propriété <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>. Pour prendre en charge de la barre de Navigation, vous devez implémenter la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> de l’objet dans le <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> méthode sur la <xref:Microsoft.VisualStudio.Package.LanguageService> classe.  
  
 Dans votre implémentation de la <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> (méthode), si le <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> est définie sur `true`, vous pouvez retourner un <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objet. Si vous ne renvoyez pas l’objet, la barre de Navigation n’est pas affichée.  
  
 L’option pour afficher la barre de Navigation peut être définie par l’utilisateur, il est donc possible pour ce contrôle doivent être réinitialisées lorsque l’affichage de l’éditeur est ouvert. L’utilisateur doit fermer et rouvrir la fenêtre d’éditeur avant que la modification ait lieu.  
  
## <a name="implementing-support-for-the-navigation-bar"></a>Mise en œuvre de la prise en charge de la barre de Navigation  
 Le <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> méthode prend deux listes (une pour chaque liste déroulante) et deux valeurs représentant la sélection actuelle dans chaque liste. Les listes et les valeurs de sélection peuvent être mis à jour, auquel cas la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> méthode doit retourner `true` pour indiquer que les listes ont été modifiés.  
  
 La sélection est modifiée dans les types de liste déroulante, la liste des membres doit être mis à jour pour refléter le nouveau type. Ce qui est affiché dans la liste des membres peut être :  
  
-   La liste des membres pour le type actuel.  
  
-   Tous les membres disponibles dans la source de fichier, mais avec tous les membres pas dans le type actuel affichent dans le texte grisé. L’utilisateur peut toujours sélectionner les membres grisée, ainsi, ils peuvent être utilisés pour la navigation rapide, mais la couleur indique qu’ils ne sont pas partie du type actuellement sélectionné.  
  
 Une implémentation de la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> méthode effectue généralement les étapes suivantes :  
  
1.  Obtenir la liste des déclarations actuelles pour le fichier source.  
  
     Il existe plusieurs manières de remplir les listes. Une approche consiste à créer une méthode personnalisée de votre version de la <xref:Microsoft.VisualStudio.Package.LanguageService> classe qui appelle le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode avec la raison de l’analyse personnalisée qui retourne une liste de toutes les déclarations. Une autre approche peut consister à appeler le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> (méthode) directement à partir de la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> méthode avec la raison de l’analyse personnalisée. Une troisième approche peut être en cache les déclarations dans les <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe retournée par la dernière opération d’analyse complète de la <xref:Microsoft.VisualStudio.Package.LanguageService> classe et de le récupérer à partir de la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> (méthode).  
  
2.  Remplir ou mettre à jour la liste des types.  
  
     Le contenu de la liste des types peut mettre à jour lorsque la source a changé ou si vous avez choisi de modifier le style du texte des types en fonction de la position actuelle du signe insertion. Notez que cette position est passée à la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> (méthode).  
  
3.  Déterminer le type pour le sélectionner dans la liste des types en fonction de la position actuelle du signe insertion.  
  
     Vous pouvez rechercher les déclarations qui ont été obtenues à l’étape 1 pour rechercher le type qui définit la position actuelle du signe insertion et puis rechercher la liste de types de ce type déterminer son index dans la liste des types.  
  
4.  Remplir ou mettre à jour la liste des membres en fonction du type sélectionné.  
  
     La liste des membres reflète ce qui est actuellement affiché dans le **membres** liste déroulante. Le contenu de la liste des membres devrez peut-être mettre à jour la source a changé ou si vous affichez uniquement les membres du type sélectionné et le type sélectionné a changé. Si vous choisissez d’afficher tous les membres dans le fichier source, le style du texte de chaque membre dans la liste doit être mis à jour si le type sélectionné a été modifié.  
  
5.  Déterminer le membre à sélectionner dans la liste des membres en fonction de la position actuelle du signe insertion.  
  
     Rechercher les déclarations qui ont été obtenues à l’étape 1 pour le membre qui contient la position actuelle du point d’insertion, puis recherche la liste des membres de ce membre déterminer son index dans la liste des membres.  
  
6.  Retourner `true` si toutes les modifications ont été apportées à la liste ou les sélections dans les listes.