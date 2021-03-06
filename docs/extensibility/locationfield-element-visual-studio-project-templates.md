---
title: "LocationField, élément (modèles de projet Visual Studio) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords: LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 33be0fde28dded57aafa04e8d6862bcd6e0cf101
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="locationfield-element-visual-studio-project-templates"></a>LocationField, élément (modèles de projet Visual Studio)
Spécifie si le **emplacement** zone de texte dans le **nouveau projet** boîte de dialogue est activée, désactivée ou masquée pour le modèle de projet.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<LocationField >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<LocationField> Enabled/Disabled/Hidden </LocationField>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Définit la catégorie du modèle et comment il s’affiche, que ce soit le **nouveau projet**.|  
  
## <a name="text-value"></a>Valeur texte  
 Une valeur texte est requise.  
  
 Les valeurs texte valides sont :  
  
-   `Enabled`, qui spécifie que la **emplacement** zone de la **nouveau projet** boîte de dialogue est activée.  
  
-   `Disabled`, qui spécifie que la **emplacement** zone de la **nouveau projet** boîte de dialogue est désactivée.  
  
-   `Hidden`, qui spécifie que la **emplacement** zone de la **nouveau projet** boîte de dialogue est masquée.  
  
## <a name="remarks"></a>Remarques  
 La valeur par défaut est `Enabled`.  
  
 Le **emplacement** zone de texte dans le **nouveau projet** boîte de dialogue permet aux utilisateurs de modifier le répertoire par défaut dans lequel les nouveaux projets sont enregistrés.  
  
 La valeur spécifiée dans le `Location` élément est respecté par la boîte de dialogue uniquement si le système de projet sous-jacent la prend en charge.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre les métadonnées d'un modèle [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <LocationField>Disabled</LocationField>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)